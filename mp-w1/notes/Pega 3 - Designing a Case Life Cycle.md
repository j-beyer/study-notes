## Case Life Cycle Design
_Business Application_: e.g. opening an account, filing an accident claim, ...  
-> build all applications with Pega to make things easier

_Case_: piece of work that delivers business outcome  
_Case Life Cycle_: opening, working steps, resolving

_Stage_: high level milestone in a case  
_Process_: series of actions or steps inside a stage

### Case Types
Metamodel for case instances

### Stages
first sense of flow, what can be done in sequence/parallel, what is start/end
_primary stage_: stages that lead to expected outcome
_happy path_: sequence of primary stages

Guidelines:
1. Stages represent significant change in case status
2. Stages usually transfer ownership
3. Names should be short and accurately describe context of the stage
4. Try to have no more than 7 stages

### Processes
Set of tasks  
Multiple processes per case are possible

__Process steps__:  
naming: like tasks (verb + noun)
max 5-7 tasks per process