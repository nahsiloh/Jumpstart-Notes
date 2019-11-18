## Creating Restful API 

-sends back data other than html - usually in JSon format



#### RESTful Constraints

- client- server Architecture
  - separation of concerns, downs not care about the UI
- stateless
  - no client-context, does not care about sessions
- cacheability
  - responses need to be defined themselves as cacheable or non-cacheable
- layered system
  - intermediate serves may be used without the client knowing about it 
- uniform interface
  - resources are identified in requests, transferred data is decoupled from db schema
  - self descriptive messages links to further resources