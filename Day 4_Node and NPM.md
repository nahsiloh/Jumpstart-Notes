5th sept 2019

## Javascript - Node and NPM

https://thoughtworks-jumpstart.gitbook.io/book/javascript/toolchain/node-and-npm

NPM = node package manager

```bash
// to create a .js doc with "Hello World" script
echo "console.log("Hello World")"> helloworld.js

// to print out the script
node helloworld.js
```



#### To install a npm package

###### Option 1

```bash
npm init
// is a basic formatter to get the structure in the package.json file
//  entry point:(index.js)
```

###### Option 2

```bash
npm install package_name
// get the name from the npm install package
```



#### Understanding version numbers in dependencies

To check dependencies version on the package.json file

https://docs.npmjs.com/files/package.json = To check the dependencies syntax

- ##### number versioning = semantic versioning (semver)

  - major version = new breaking change 

    i.e 1.0.0 to 2.0.0

  - minor version = increased when new non breaking change is added

    i.e 1.1.0 to 1.2.0

  - patch version = increased when new bug fix is added

    i.e 1.1.7 to 1.1.8

    

- ##### special characters - in the package.json file

  ```
  "moment": "2.99.999"
  
  // install the latest Minor and Patch versions
  "moment": "^2.99.999"
  
  //pull the latest Patch versions
  "moment": "~2.99.999"
  
  To Update latest major version use:
  npm update 23.2.1
  ```

  ** DO NOT MODIFY package-lock.json** = shows the specific version that has been installed



![1567653406024](C:\Users\lisha\AppData\Roaming\Typora\typora-user-images\1567653406024.png)



- Development dependency is for developer usage only, where it does not affect the user-end = should always place files that the team should use. 

  eg. eslint , testing dependencies



##### STEPS

1. npm init = to set up the package.json file

2. npm install cows = to install the package name cows

3. to import the package in the .js file

   `const cows = require("cows")`