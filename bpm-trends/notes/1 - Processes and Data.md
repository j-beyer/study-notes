## Importance of Data Modeling in BPM
Processes integrate:
- Resources
- Decision Making
- Control Flow
- Time Management
- __Data__

__Problems__:
- no conceptual model for mapping between data in _business processes_ and their corresponding _data entities_
- different domains (BPM vs IS)
- data in processes remains hidden inside IT systems

__Motivation__:
- data is driving factor of business processes (process information, decision making)

#### Types of Data
- _Application data_: real world data, out of scope of process
- _Process-relevant data_: process variables inside data objects
- _Process control data_: current execution state/history of process

__Process-relevant data__: 
- operational data: needed for activity execution, e.g. patient name, age, gender
- reference data: identifies instance, e.g. social security number
- decision data: subset of operational data needed for decision making
- domain knowledge: rules, laws etc., that are external and independent of instance
- aggregated data: to measure KPIs 
- _business rules_: define/constrain behavior of business aspect
- _temporal constraints_: define temporal relations to regulate process execution

## Data Modeling in BPMN
- Data Objects (local to process instance)
- Data Inputs/Outputs (requirements and results of one (sub-)process)
- Data Stores (persist information beyond lifetime of process instance)
- Data Object Collections (if all instances of specific data type, e.g. order item, need to be present at the same time)
- Read/Write by activities
- States, State Transitions and corresponding Object Life Cycles

There exist __Workflow Data Patterns__ to unify handling of:
- Data visibilty
- Data interaction
- Data transfer
- Data-based routing

__Weaknesses__:
- Concurrency / Transactional behavior, e.g. 2 parallel activities, each with r/w access to same data object
- Complex / compound data types, e.g. Customer-Order-Item relation

## Activity Centric vs. Data Centric Process Models
___Activity centric process modeling___ focuses on activity completion and control flow  
Data is modeled with data objects, data flow, and read/write access by activities

_Challenges_:
- OLC Conformance
- Complex data dependencies, mapping to DB queries
- Complex data objects
- Connection with external information systems

___Data centric process modeling___ results in loosely structured processes driven by decisions
Data is modeled by identifying domain-relevant entities with relationships and lifecycles, and an information model including constraints and goals

___Artifact centric process modeling___ contains artifact types consisting of an information model (business artifact) and its lifecycle in association to tasks in a process model

### Comparison
|      |Activity centric|Data centric|
|------|----------------|------------|
|driver|control flow|data entities|
|data manipulation|by activities|activities are associated to data entities and their state changes|
|process structure|structured, repetitive|loosely structured, knowledge-intensive|
|information model|_none_|process-relevant-data|
|standard support|mainstream modeling languages (BPMN)|ad-hoc solutions, limited support|
|drawback|data is mostly hidden|no regard for activities that do not work with data|

## Research
Integration of existing processes and data models  
Modeling requirements for data  
Mapping database content to process-relevant data  


