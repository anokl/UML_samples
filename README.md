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

Plant UML example:
```
class A
{
  + void PublicFunction()
  - void PrivateFunction()
  # void ProtectedFunction()
}
```

![Class Diagram](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/anokl/UML_samples/master/UML/visibility.uml)


### Association
### Association
### Aggregation
### Composition
### Multiplicity
### Dependecy
### Generalization
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
