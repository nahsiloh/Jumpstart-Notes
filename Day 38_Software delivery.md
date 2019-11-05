22nd Oct 2019

## Software delivery

UML - unified modelling language

WATERFALL vs AGILE



##### Agile manifesto and principles

- Shu-ha-ri theory of learning

- Agile methodologies

  - XP 
    - TDD
    - Pair programming
  - SCRUM
    - sprint
    - product owner
  - KANBAN
    - story board

- the coin game experiment

- cross functional teams

  

#### User Stories

- story depth = epic vs user stories

- should be small enough for the time delivery to be estimated
- small enough to be tested independently
- ideal size: fit 1 day development work so that it is demonstrable 
- focus on business value



##### Story writing

- As a .... so that 

- should be short and concise 

- ###### I.N.V.E.S.T

  - “I” ndependent (of all others)
  - “N” egotiable (not a specific contract for features)
  - “V” aluable (or [vertical](http://guide.agilealliance.org/guide/incremental.html))
  - “E” stimable (to a good approximation)
  - “S” mall (so as to fit within an iteration)
  - “T” estable (in principle, even if there isn’t a test for it yet)

- should not specify implementation detail



##### Vertical Slicing

- contains a range of frontend and backend scope = eg. create a login page

  

##### Walking skeleton



##### Acceptance Criteria

- define the boundaries for a user story/ feature
  - know when to stop writing functionality 
  - and define the tests

- no strict convention - specifies in plain language how the programmer or tester will know the task is completed - however should stick to one format

  "Given ..... , When....., Then....."

- set of rules which covers the system's behavior, and from which scenarios can be derived

- should be clear and differentiated between the acceptance criteria (more generic, eg. in the describe block) and the test scenarios (more specific eg. in the it block)