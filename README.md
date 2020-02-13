# UML samples
## Types of modelling
There are two basic types of modeling: structural and behavioral. 
The structural modeling focuses on the static structure of the system, its components and their relations. The structure diagrams in UML consist of the following:
* class diagram
* component diagram
* package diagram
* deployment diagram

The behavioral modelling describes the dynamic behaviour of the system, that is how the components interact and how the system changes over time. The behavoiral diagrams in UML include:
* Use case diagram
* Sequence diagram
* Activity diagram
## Class diagrams
### Visibility
Notation | Visibility
---------| ---------
\+ | Public
\# | Protected
\- | Private
\~ | Package

Plant UML syntax:
```
@startuml
class A
{
  + void PublicFunction()
  - void PrivateFunction()
  # void ProtectedFunction()
}
@startuml
```
Generated diagram:

![Class Diagram](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/anokl/UML_samples/master/UML/visibility.puml)


### Association
Is a generic term for a semantic relation between classes either unidirectional or bidirectionl. Usually, the bidirectional relation is assumed if no arrows are specified. 

Plant UML syntax:
```
@startuml
class Hand {}
class Finger {}

Hand-Finger
@enduml
```
Generated diagram:

![Class Diagram](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/anokl/UML_samples/master/UML/association.puml)

In class diagrams the directional relation should be interpreted as a navigability and depicted as a openhead arrow. 
The following diagram means that Finger is navigable from Hand.  

![Class Diagram](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/anokl/UML_samples/master/UML/directional_association.puml)

Plant UML syntax:
```
@startuml
class Hand {}
class Finger {}

Hand->Finger
@enduml
```
### Multiplicity

In UML the number of objects that participate in a relation is called multiplicity: 

Notation | Multiplicty
---------| ---------
1 | One and only one
\*  | Zero or more
1..\* | One or more
0..1 | Zero or one

In the example above, a humanoid hand usually have at most 5 fingures. In UML this relation can be depicted as following:

![Class Diagram](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/anokl/UML_samples/master/UML/multiplicity.puml)

Plant UML syntax:
```
@startuml
class Hand {}
class Finger {}

Hand "1" --> "0..5" Finger
@enduml
```

### Aggregation \ Composition
Aggregation and composition are relations with additional semantic meaning. Aggregation relation assumes that a child object can exist independently of a parent object. In composition relation, a child can only exist in relation with a parent. 
Graphically, agregation and composition are represented by a hollow and a filled dimond respectively.

This two notions are very domain specific. In the example above, a finger probably cannot exist separated from hand (aggregation) but a ring can be either related to a finger or can be lost and therefore can exist on its own (composition). 

![Class Diagram](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/anokl/UML_samples/master/UML/aggregation_composition.puml)

Plant UML syntax:

```
@startuml
class Hand {}
class Finger {}

Hand "1" --> "0..5" Finger
Finger "1" --> "0..*" Ring
@enduml
```

### Dependecy
Dependency is another type of relationship between classes. This kind of relationship means that a class needs another class but does not contain its reference. This relation is weaker than assotiation. Typical, the assotiation may exist when a member function of a class takes another class as a parameter or returns it as a result of a member function. Grafically it is represented by a dashed arrow:

![Class Diagram](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/anokl/UML_samples/master/UML/dependency.puml)

```
@startuml
class PeerDirectory
{    
   +std::vector<Peer> GetPeersHandlingMessage(MessageId messageId)
}

class Peer
{
   +string PeerName;
   +string ip;
   +string protocol;
   +int port;
}

PeerDirectory..>Peer
@enduml
```

### Generalization
The generalization in terms of OOP is an inheritence. The inheritence may appear when a domain includes multiple classes of similar nature. The common attributes or member functions of such classes are moved to a common base class:

![Class Diagram](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/anokl/UML_samples/master/UML/genralization.puml)

```
@startuml
Transport<|--PeerToPeerTransport
Transport<|--MulticastTransport
@enduml
```

### Realization
## Component diagrams
## Package diagrams
## Deployment diagrams
## Use case diagrams
## Sequence diagrams
### Lifeline
### Activation boxes
### Messages
### Loops
### Optional flows
### Alternative flows
## Activity diagrams
### Start / end nodes
### Action / control flows
### Decision / merge nodes
### Fork / join nodes
