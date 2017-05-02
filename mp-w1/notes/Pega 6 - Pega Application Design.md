## Building Blocks of a Pega Application
### Rules and Rule Types
... tell the application how to create, handle, close cases  
... are used to generate application code  
... describe specific aspects of case behavior  
... (are similar to classes in Java)

__Flow Rules__ are constraints that describe the order of the steps of a process  
__Rule Types__ are a schema for rules for specific case behaviors

Rules introduce modularity into the application design, providing the following benefits:
- Versioning
- Delegation
- Reuse

### Rulesets
Sets of Rules used in an application  
__Versioning__: Rulesets are only updated by creating new ruleset versions (uses SemVer)

### Ruleset Stacks
Ordered sequence of rulesets with listed version  
containing also all lower minor/patch versions for major version  
Each application version comes with a new ruleset stack (with new ruleset versions)

### Class hierarchy
Rules are grouped into classes by reusability  
Class types:
- rules in a __work class__ describe __how to process a case__
- rules in a __integration class__ describe __how the application interacts with other systems__
- rules in a __data class__ describe the __data objects used in the application__

Inheritance:
- each case type has a class inheriting from the work class
- each data object has a class inheriting from the data class

The ___Class Hierarchy___ comprises the application and determines the reuse of rules.

### Creating and Updating rules
__Creation__: in the New Record form (e.g. +Create), enter: rule type - 
identifier - class - ruleset

__Updating__: via check out & check in, locks rule against access from other developers during edit  
alternatively: private edit to only change the rule in my personal ruleset  
old rulesets are locked by default

## Reuse by Inheritance - IMPORTANT
### Pattern Inheritance
_Business_ Relationship  
Rule classes throughout an organization, divided in layers:
1) __organization__ layer: all classes for applications in the entire organization, generic data/integration
2) __division__ layer
3) __class group__: contains all case types of an application
4) __rules for specific case type__
### Directed Inheritance
_Functional_ Relationship  
Reuse rules from other applications, and from standard Pega platform
### Reuse
search Rule in PI-Parents, if not found:  
search in DI parent, if not found:  
use DI parent as base for another PI parent search, etc.  
repeat until @baseclass
### View Inheritance
in the Application Explorer,, select class in application scoping control
Right Click -> Inheritance

## Assessing Guardrail Compliance
(Integrated monitoring of application configurations and rules, similar to Sonar)
Overview of compliance with standards and best practices by __compliance score__

Open: Designer Studio > Application > Guardrails  
Thresholds: score > 90: good,  
score >= 80: needs review,  
score < 80: needs immediate review

__Warning Summary__ tab provides overview of rule warnings per rule type

__Compliance Details__ tab provides analysis of risk areas:
- Warning impact: rules with severe/moderate warnings
- Warning age
- Operator/Developer that caused the warning

### Addressing violations
__resolve__: eliminate cause of violation (e.g. disable draft mode)

__justify__: when requirement/design approach leads to warning (e.g. justify activity rule for database access)  
review/edit -> Add justification -> enter text
-> OK