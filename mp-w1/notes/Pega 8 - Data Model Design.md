## Data Elements in Pega Apps
Data is needed for making decisions for processing and resolving cases  
Elements that store data are called _properties_ or _fields_

Case Types have __Data Models__
A data model is build from single value elements and __Data Objects__

__Properties__ can be single values or data objects  
There are two property modes:
- Value modes: single piece of information (total price), no correlation to other properties
    - single value
    - value list (ordered text values)
    - value group (unordered text values)
- Page modes: data object (customer) as context for single values
    - page
    - page list (numerically ordered)
    - page group (semantically ordered)

### Managing Properties
__Data Explorer__:  
Browse, add and remove data types  
Pega provides standard data types  
Extend data types that only partially fit your needs (create -> advanced settings -> parent class)

__Data Model tab__:  
Browse, add and remove properties (fields) from case types and data types  
Specify field types for new fields
- simple
- fancy (attachment upload, map location, user reference)
- complex (page or page list)

__Property rule form__:  
Contains property definition  
Property definitions are rules  
_Data Access_: manual (UI) vs. automatic  
_Display and validation_: UI control type (text input, picker), specify valid values  
Pega standard property rules: 
- px: special properties that can only be read
- py: usable in application
- pz: internal system proessing, can only be read

### Referencing Properties
Reference by prefixing with "."  
Examples:
- Value Mode
    - .OrderDate (_single value_)
    - .Phone(Mobile) (_subscript of entry in group property_)
    - .DiscountCode(1) (_index of entry in list property_)
- Page Mode
    - .Customer (_page_)
    - .Address(Work) (_subscript of entry in page group_)
    - .LineItems(3) (_index of page in page list_)

Concatenation for specific property on a page, ex.: .Address(Work).City

### Defining Properties
__Create Data Types__ in the Data sidebar  
__Manage Properties (Fields)__ in data types in the Data Model tab in Case Designer  
__ Define lists of data entry options__ in the Data Model tab in Case Designer by using the _Picklist_ data type

## Setting Property Values Automatically
Ex.: provide default values, combine "first name" and "last name" field into full name

### Data Transforms
_Mapping data from source to target_  
Ex.: Copy Shipping Address data to Billing Address data  
Can be called in multiple ways (Flow action rule, connector)  
pyDefault initializes property values upon case creation  
Iterate over page lists and page groups, copy pages

__Setting Values__:  
Data Transformation consists of:
- Action (Set, When, Remove)
- Target (to be checked/modified)
- Relation (set A _equal to_ B)
- Source (Value used for transformation)

__pyDefault__:  
Ex.: in a claim application, set "Date of Loss" to today per default

__Superclassing__:
Transform/Default values should be applied on the highest class level that contains the field  
create a data transform with the same name at each level  
and select __Call super data transform__ checkbox

## Setting Property Values Declaratively
Ex.: Updating total price, when amount of ordered items is changed

__Declarative vs. Procedural processing__  
_Declarative processing_ allows to configure computational dependencies between properties, that are automatically updated on dependent value change  
Updates only occur when triggered in the app  
-> _trigger events_ are defined using declarative rules

_Procedural processing_ depends upon rules (data transforms, activities, UI rules)  
actively instruct app when to look for _trigger event_  
Ex.: data transform that calculates order total from amount x single price  
Makes maintenance harder, problem: updates only occur upon user changes

__Declare Expressions__ are used to update property values in forms  
contain expression, target and source (just like data transform, but procedural)
system monitors changes in source values and updates the target according to the expression

__Declarative Networks__ make it possible for Declare Expressions to reference other Declare Expressions (similar to DRG)  
Ex.:  
Item Price * Qty = Item Total  
Item Total 1 + Item Total 2 + Item Total 3 = Order Total  
Can be accessed in Designer Studio under __Process & Rules > Business Rules__

__Forward and Backward Chaining__  
_Forward chaining_ is when a declare expression updates the target upon source change (declare expression default)  
_Backward chaining_ only calculates/updates the target expression, when the target expression is actually used/referenced  
___Performance___ can be optimized by using the chaining methods according to the situation  

### Setting property values with declare expressions
1. Create the declare expression (select target expression in App Explorer, right click -> define expression)
2. Configure expression in Expression tab with Target, Computation Type and Expression
3. Specify chaining in the Change Tracking tab (Whenever Inputs Change = forward)

## Data propagation between cases
share information with subcases or spin-off cases  
provide relevant information to case workers  
Ex.: Purchase Request case -> inventory selection subcase: product id and quantity must be passed  
Copy upon (sub|spin-off) case instantiation, copy does not get updated if original is updated in parent  
Propagation can pass properties directly, or via data transform if logic step is needed

__Define data propagation__:  
Case Explorer -> Settings > Data propagation  
Add Property for each property that should be propagated  
Apply data transform if wanted

__Configure Data Propagation for create case utility__:  
Case Explorer -> select parent case -> select step that uses "create case"  
Specify data transform

## Reviewing Application Data
_Verify that the data generated during application execution is correct_  
Access Data in Memory using the Clipboard tool  

Information -> data element (name and value) -> page
The Clipboard stores pages in memory during case processing  

### pyWorkPage
special page on the clipboard  
stores all the data generated during case creation and processing  
user defined pages are stored as __embedded pages__ in the pyWorkPage
used for debugging data state in applications  
child cases also have __pyWorkCover__ in the clipboard, which contains all data from the parent case