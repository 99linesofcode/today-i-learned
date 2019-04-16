# Communicating Architecture

## [Kruchten's 4 + 1 architectural view model](https://en.wikipedia.org/wiki/4%2B1_architectural_view_model)
> Describing the architecture of software-intensive systems, based on the use of multiple,
> concurrent views.

### Logical View
Concerned with the fuctionality that the system provides to the end-users.

- [UML Class Diagram](class_diagram.md)
- [UML State Diagram](https://en.wikipedia.org/wiki/State_diagram)

### Process View
Deals with the dynamic aspects of the system, explaining the system's processes and how they
communicate and focuses on the runtime behavior of the system. It addresses things like concurrency,
distribution, integrators, performance, scalability, etc.

- [UML Sequence Diagram](https://en.wikipedia.org/wiki/Sequence_diagram)
- [UML Activity Diagram](https://en.wikipedia.org/wiki/Activity_diagram)

### Development View
Illustrates a system from the programmer's perspective and is concerned with software management.

- [UML Component Diagram](https://en.wikipedia.org/wiki/Component_diagram)
- [UML Package Diagram](https://en.wikipedia.org/wiki/Package_diagram)

### Physical View
Depicts the system from a system engineer's point of view. It is concerned with the topology of
software components on the physical layer as well as the physical connections between these
components.

- [UML Deployment Diagram](https://en.wikipedia.org/wiki/Deployment_diagram)

### Scenario's
The description of an architecture illustrated using a small set of use cases, or scenario's, which
become a fifth view. The scenario's describe sequences of interactions between objects and between
processes. They are used to identify architectural elements and to illustrated and validate the
architecture design. Additionally, they can serve as a starting point for tests.

## UML diagrams

### Component Diagram
Depict how components of a software system are wired together to form larger components. They are
used to illustrate the structure of arbitrarily complex systems.

> Component diagrams are concerned with the components of the system. Components are independent,
> encapsulated units within a system. Each component provides an interface for other components to
> interact with it.

The component diagram depicts the individual components and their relationships with other
components through ball and socket connections that represent the provided and required interfaces.

When building a component diagram, the first step is to identify the main objects in the system.
Next, you would identify all the relevant libraries that you would need for your system. Finally,
you come up with the relationships found between these components.

### Packaging Diagram
Depicts the dependencies between the packages that make up a model.

> A package groups together elements of your software that are related. A package also defines a
> namespace for the elements it contains. In example: in a videogame you might ahve several classes
> that handle different functionality for a player, like movement, combat or dialogue. All of these
> functionalities are related to the player (the package).

### Deployment Diagram
Models the physical deployment of artifacts (physical result of the development process) on nodes.
It describes hardware components.

> A software release is more than just lines of code bundled together. It involves separate
> libraries, an executable (usually), an installer, configuration files and many other different
> pieces. A deployment diagram is used to visualize these deployment details for a software system.

#### Specification Level Diagram
#### Instance Level diagram

### Activity Diagram
Graphical representation of workflows or stepwise activities and actions with support for choice,
interation and concurrency. Activity diagrams are intended to model both computational and
organizational processes (ie. workflows). They show the overall flow of control.

#### Partitions
Partitions divide activities up into different categories, sucha s where it occurs, or the user role
involved. Swimlanes are used in an activity diagram to display these partitions.
