## Case Types and Cases
Templates and instances of work (business transactions)
Multiple case types and their relationships build up business processes

Case types contain:
- Life cycles of transaction instances
- data structures (patient information, procesdure information)
- processes (reviewing/approving/rejecting claims)
- tasks
- UIs (user forms for attaching documents)

New claim -> new instance (new case)

### Case Type Relationships
Ex.: Candidate Application case --creates--> Onboarding case (if successful) --has-child--> Payroll Setup case

__Top-level__ case types do not have parent types, but can cover/become parent of other case types  
__Child__ case types are covered by parent case types, must be completed before the parent can be resolved

Ex. 2: Auto Insurance App
- Accident Claim case type (_top-level_)
    - Vehicle Damage case type (_child_)
    - Body Injury case type (_child_)

Reports can associate a parent case with its child cases (e.g. Accident Claim document)  
Child cases can be processed in parallel by different parties (e.g. Repair Shop for Vehicle Damage, Medical Provider for Body Injury)

### Adding case types
#### Top-Level
In __Case Designer__, click __Cases__ in navigation panel  
__+ Add a case type__  
Enter __Name__, configure __Advanced Settings__
#### Child
___Adding new child case type___
In __Case Type Explorer__, select __options__ from a parent case type  
__Add child case type__ -> __new case type__  
...

___Adding an existing child case type___  
In __Case Type Explorer__, select __options__ from a parent case type  
__Add child case type__ -> __Existing case type__  
...

### Creating a case during case processing
to begin a new process instance / a new portion of an existing instance

__Case Designer__ -> __Life Cycle__ tab -> __Add step__  
__More > Utilities > Create Case__  
Configure the Create Case shape:
- Top-level
- Child
- Multiple Child cases

Add a __Data Transform__ that sets inition property values  
__Audit Note__: add field value that will be added to history (audit trail) during processing
