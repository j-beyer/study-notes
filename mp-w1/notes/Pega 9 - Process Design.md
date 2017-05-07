## Activities
_Rules that describe logic for automated behavior_

### Usage of Activities in Applications
Describe procedural logic, simliar to programming languages  
Ex.: Routing the case, updating status, send request to external system, write to log/database

Activities contain __Steps__ that each execute a __Method__  
Examples for methods: 
- Set value in property
- Create page
- Delete page from clipboard
- Update a property via data transform

### The Activity Execution Model
Activities execute their steps in sequence (by default)  
loops, conditions and jumps are possible  

Activities can access data from:
- primary page (data context for activity, clipboard page that has same class as activity applies-to-class)
- step page (data context for specific step, by default the primary page becomes the step page)
- parameter page (parameter names and values to communicate with callers)

__Activity Parameters__ promote reuse (simliar as function parameters in programming)  
are listed in the Parameters tab of the Activity form  
can be assigned values to serve as activity _output_

### API Activities
Pega-predefined activities for performing standard functions  
Ex.: CorrNew (create and send e-mails), AddWork (create new case instance), UpdateStatus (of case instance)  
Subgroup: Process API, to start/advance cases without user input

### Activity Reuse and Libraries
Activities can quickly become too complex and hard to maintain  
Alternatives/Solutions:
- for data manipulation: use Data Transforms instead
- for data calculation: use Declare Expressions instead
- for database queries: use Report Definitions instead
- try to consider standard API activities for your requirement

## Routing Assignments
_Assigning tasks to users with roles that are most qualifed for the work_

Assignment Tasks (green) have to be completed by a user  
Routing instructions in the task determine the user type  
Ex.: Customer Service Representative enters information, Manager works on customers request

### Worklists and Workbaskets
A __worklist__ contains all open tasks for a user  
Can be accessed from user portals

A __workbasket__ contains queued tasks for a __work group__  
Team members can select tasks or be assigned by a manager

### Routers
_Routers_ are special activity types controlling routing via parameters  
contain a _routing destination_ and _assignment type_

Standard routing: send to user worklist or to group workbasket  
Routing by role: send to a user that has the specified role  
Routing by user skill: send to a user in a group with specific skills (e.g., speak a certain language)  
Decision routing: send to user according to decision rule output

### Configuring Routing
- Assignment steps in case life cycle
- Assignment shape in flow diagram
- Approval Process SmartShape

__Life Cycle__: Assignment step -> General -> Route to  
_(Specific user = to worklist, Work queue = by role)_  
Custom: Specify activity that creates assignment, and activity that determines assignment

__Assignment shape__: Right click -> Properties -> Routing

__Approval process__: Right click -> Approval Properties  
Single-level approval: assign to worklist, workbasket, or approval manager  
Cascading approval: based on reporting structure or decision table, assigned to approval manager
