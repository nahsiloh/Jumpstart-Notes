24th October 2019

## Devops

##### Continuous Integration

- software development practice where members of a team integrate their work frequently



##### Deployment

- taking software features you build and make it available to intended users
- labour intensive - may require linting, unit test, security scans, build, setup environment, E2E tests
- manual deployment is prone to mistakes and very time consuming



##### Continuous Deployment

- tests becomes ever more important



### Circle Ci

- every commit triggers an automated build and test 
- if build fails, everybody in the team will be notified



- requires a docker

##### How to deploy on Circle Ci

https://circleci.com/docs/2.0/deployment-integrations/#heroku

1. create `.circleci` folder



`heroku authorizations:create`

- will generate the token for the HEROKU_API_KEY

  

![1571908377674](C:\Users\lisha\AppData\Roaming\Typora\typora-user-images\1571908377674.png)

![1571908398257](C:\Users\lisha\AppData\Roaming\Typora\typora-user-images\1571908398257.png)

![1571908605072](C:\Users\lisha\AppData\Roaming\Typora\typora-user-images\1571908605072.png)



```yaml
version: 2
jobs:
  test:
    working_directory: ~/app
    docker:
      - image: circleci/node:12.13.0
    steps:
      - checkout
      - restore_cache:
          key: dependency-cache-{{ checksum "package-lock.json" }}
      - run:
          name: "install package manager"
          command: "npm install"
      - save_cache:
          key: dependency-cache-{{ checksum "package-lock.json" }}
          paths:
            - ./node_modules
      - run:
          name: "run test"
          command: "npm test"
  deploy:
    docker:
      - image: buildpack-deps:trusty
    steps:
      - checkout
      - run:
          name: Deploy Master to Heroku
          command: |
            git push https://heroku:$HEROKU_API_KEY@git.heroku.com/$HEROKU_APP_NAME.git master

workflows:
  version: 2
  runTest:
    jobs:
      - test
      - deploy:
          requires:
            - test
```



https://hub.docker.com/r/circleci/node

- to cache the npm install, add the restore_cache and save_cache
- sometimes, the npm install may take awhile



- checksum - its like a hash for the files, to check if there are any updates



#### CircleCi for frontend



![1571983049744](C:\Users\lisha\AppData\Roaming\Typora\typora-user-images\1571983049744.png)



need to get OAuth token from netlify

![1571983106362](C:\Users\lisha\AppData\Roaming\Typora\typora-user-images\1571983106362.png)



- to check in terminal

`export NETLIFY_AUTH_TOKEN=<API KEY>`



- add environment variable to circleCi