## Automating Decisions
_ensures consistent decision making, increases performance_

### Decision Types
__Business Rules__:  
direct application flow, hide/display form elements, calculate property values  
- when conditions: like if/else in programming
- map values: 2d matrix, 2 inputs provide row and column, return intersected field
- decision tables: if all fields in input row are true, return output value for row
- decision trees: series of if-then conditions in tree structure

tables and trees are used to direct control flow, called from decision shapes  
can also set property values as part of declare expression  
can test any number of values

__Decision Management Rules__:  
analyuze customer behavior, used for customer propositions
- Strategies: consists fo the following, personalized result to customer (e.g. credit card offer based on spending pattern, income, ...)
- Interactions: define parameters and outcomes for strategy
- Predictive models: predict behavior based on customer data
- Adaptive models: capture customer responses and adapt/generate predictions
- Scorecards: uses conditions and combiner to return score and segment (e.g., segment customers based on age and income, recommend a different credit card)

## Configuring When Rules
_true/false decisions_  
compare property values with other values/constants  
in control flow: used as xor with 2 outcomes  
in UI forms: used to show/hide certain inputs based on conditions  
in data transforms: execute transform steps based on condition

### When Rule form
organizes set of true/false checks into tree structure  
Conditions-Tab: enter conditions combined with AND or OR  
Advanced-Tab: see condition as logic string

Double click to add condition  
right-click or Actions-Button to open Actions Menu  
in Actions Menu, insert more conditions or insert group for sub-nodes

## Configuring Decision Tables and Trees
### Tables
Reference DT in decision shape to determine the outgoing flow  
Also usable in declare expressions, activities, and routers

Specify: 
- Condition properties
- Conditions and return value per row
- otherwise-value

Application Explorer > +Create > Decision > Decision Table

### Trees
contain if-then-else logic  
comparison value - comparison operator - action - next value  
action can be return, continue, otherwise  
add rows with crosshair icon

### Unit testing
Actions > Run: test with certain input values  
Test for conflicts (unreachable branches) with __Show conflicts__  
Test for completeness (uncovered branches) with __Show completeness__

