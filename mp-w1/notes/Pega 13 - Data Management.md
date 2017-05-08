## Caching with data pages
_Data pages_ retrieve data for the app and cache it on the clipboard  
the _structure_ can be page or list  
a _scope_ defines the acces to the data page  
the _refresh strategy_ defines when the page is reloaded  
a _source_ provides the data - e.g. database table

Data Explorer > right click > Add data page  
adds a new data page rule, defining structure, scope, source and refresh strategy

Scope: 
- thread: in context of particular case
- requestor: in context of user session
- node: in contet of phyiscal node (jvm), available for all users of applications on that node

Source:
- Connector (to external source, provides possibiltiy for input/output data transform)
- Data transform
- Report definition (list of data objects in app)
- Look-up (data object in app)
- Load activity (otherwise)

Load Management > Refresh strategy

## Reference Data
defines permitted values for input fields  
_references_ master data (key business entities)  
can be stored in __local data storage__

???

## Integrating external systems

### Connectors
Ex.: bank accesses credit agency system to verify customers credit score  

Data Pages read (pull) data from external systems  
Activities write (push) data to external systems

- Data Page or Activity - specifies connector and input/output data transforms
- Data Transforms - maps app data to integration clipboard
- Connector rule - invokes service, handles request/response
- Mapping rule - parse incoming messages / build outgoing messages

Supported Connector Formats: e.g. SOAP, REST, JMS, MQ, File

### Services
_Expose services that expose specific data or functionality from Pega_  
Service Listener: 
1) recieves request  
2) determines service that should be called
3) instantiates it and establishes requestor (processing and data belonging to the request)
4) returns response

### Connecting to a database
using __SQL connector__:  
requires you to write SQL  
needed for advanced queries, vendor-specific SQL syntax

using __Database Table Class Mapping tool__:  
builds up data class, database table instance, and link between those  
data mapping that lets you directly access database tables 

Designer Studio > Data Model > Classes & Properties > Database Class Mappings

## Creating a Connector
Using Connector Wizards:
1) Upload Service metadata
2) Configure integration
3) Select methods
4) Generate records

Designer Studio > Integration > Connectors > Create XY Integration (creates new connector)  
Designer Studio > Application > Tools > All Wizards (shows all wizards used in app)

__Reading data__:
1) Create Data Page 
2) Select Connector as Source
3) Specify Type and Name

__Writing data__:
1) Add Integrator shape and configure its activity:
    1) Set up integration clipboard page under Pages & Classes
    2) Create new page
    3) Add data transforms
    4) Invoke connector
