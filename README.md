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

![UML](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/anokl/UML_samples/master/UML/visibility.puml)


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

![UML](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/anokl/UML_samples/master/UML/association.puml)

In class diagrams the directional relation should be interpreted as a navigability and depicted as a openhead arrow. 
The following diagram means that Finger is navigable from Hand.  

![UML](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/anokl/UML_samples/master/UML/directional_association.puml)

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

![UML](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/anokl/UML_samples/master/UML/multiplicity.puml)

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

![UML](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/anokl/UML_samples/master/UML/aggregation_composition.puml)

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

![UML](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/anokl/UML_samples/master/UML/dependency.puml)

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

![UML](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/anokl/UML_samples/master/UML/generalization.puml)

```
@startuml
Transport<|--PeerToPeerTransport
Transport<|--MulticastTransport
@enduml
```

### Realization

Similar to generalization, realization in terms of OOP denotes an implementation of an interface:

![UML](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/anokl/UML_samples/master/UML/realization.puml)

```
@startuml
interface IHardwareCommChannel
IHardwareCommChannel<|..CommChannel
IHardwareCommChannel<|..SimulatedCommChannel
@enduml
```
## Sequence diagrams

Sequence diagrams visualize how components in a software system interact. 

### Lifeline

In sequence diagram an object is graphically represented by rectangle. The lifeline of an object goes down from the center of the rectangle. In sequence diagram we manipulate objects and not classes (object is an instance of a class). Full object name is composed of the object name and its class name separated by a colum. This rule is often ignored and simple class names are used. 

![UML](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/anokl/UML_samples/master/UML/lifeline.puml)

``` 
@startuml
Bus--->Bus
@enduml
```

### Activation boxes
Activation boxes on object liftime shows the periode when the object is completing a task. The longer the box the longer the task. 
A task is usually activated by a messag coming from another object but an object may also activate itself:


![UML](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/anokl/UML_samples/master/UML/activation_boxes.puml)

```
@startuml
Client -> Bus: SendMessage
activate Bus
Bus -> Directory: GetPeersHandlingMessage
activate Directory
Directory->Bus: <<List of peers>>
deactivate Directory
Bus->Transport: SendMessageToPeers
activate Transport
Transport->Bus
deactivate Transport
Bus->Client
deactivate Bus
@enduml
```

### Messages
On sequence diagram, objects cmmunicate and activate each other with messages. Messages are graphically represented by arrows. There are three types of messages: 

![UML](https://github.com/anokl/UML_samples/blob/master/UML/arrow_types.png)

### Loops
Sometimes, the same task must be executed multiple times. For instance, when it is performed over elements of a collection. Just like in majorty of imperative programming langauges, this repetitve actions can be expressed as loops:

![UML](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/anokl/UML_samples/master/UML/loop.puml)


### Optional and alternative flows
Optional and alternative flows allows to model alternatives in sequence diagrams. 
Optional flow is very similar to if statement in imprerative programing language. 

![UML](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/anokl/UML_samples/master/UML/optional_flow.puml)

```
@startuml
MessageDispatcher -> Directory: PeerStarted
activate Directory
Directory -> Directory : RegisterPeer
alt Master directory
Directory -> Transport: SendSnapshot
end
return
@enduml
```

Alternative flow is similar to switch statement:

![UML](http://www.plantuml.com/plantuml/proxy?src=https://github.com/anokl/UML_samples/blob/master/UML/alternative_flow.puml)

```
@startuml
View->Controller: event

activate Controller
alt Tool navigate
Controller->Controller: navigation
else Tool contrast
Controller->Controller: contrast change
else Tool rotation
Controller->Controller: rotate
end
return
@enduml
```

### Alternative flows

## Component diagrams
## Package diagrams
## Deployment diagrams
## Use case diagrams

## Activity diagrams
### Start / end nodes
### Action / control flows
### Decision / merge nodes
### Fork / join nodes
