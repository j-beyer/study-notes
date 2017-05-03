## Motivation 
Processes act on single items  
High costs / bad performance where expensive tasks are executed once per case  
when they could be done once per multiple cases (in batch) instead  
Ex.: set-up costs, transportation costs, ...  

Idea: Batch task view with information for each instance

#### Requirements Framework
1) Process model -> Enabled activity instance per case
2) Batch creation -> collect all activity instance data (Grouping, Scheduling, Batch Assignment, ...)
3) Batch execution -> execute activity instances in batch (Activation Mechanism, Execution Strategy, ...)
4) Context (Adaptation, Variability)

## Batch Activities in Business Processes
- New BPMN activity type (standard conform)
- language independent batch configuration parameters

Metamodel:
|Batch Model | _is property of_ | Activity |
|-|-|-|
|___has___||___has___|
|__Batch Cluster__|___contains___|__Activity Instance__|

__Activation Rule__:  
on EVENT xy, if CONDITION z, do ACTION a  
Different types possible, e.g. Threshold Rule:  
Event = instance-size increased, or timer event  
Condition = instances > given number, or lifetime > given waitingTime  
Action = enable batch task execution  

__Life Cycle__:  
- init (-> ready, maxloaded)
- ready (-> maxloaded, running)
- maxloaded (-> running)
- running (-> terminated)
- terminated

### Grouping instances (Extension of Batch Activity)
"Group Activity" shape around connected activities  
Grouping is based on Data Views of Process-relevant Data Objects  
Ex.: Order in retail process -> group based on SameCustomer Data View  
SameCustomer is a _projection_ on (name, address)  
Instances, where the view holds the same values, are clustered together