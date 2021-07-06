Talk: Does CAP Theorem Apply To Microservices - https://www.youtube.com/watch?v=PgHMtMmSn9s

### CAP Theorem

If you have two nodes that have the same data replicated to eachother.

Consistency says if one node goes down you reject a data change if one of the two nodes is down.

Availability says if one node goes down, you accept the change and you will eventually be consistent when the node comes back up.

Partition Tolerance is how the cluster continues to work despite communication breakdowns.

### Microservices

Loosely coupled service oriented architecture with bounded contexts - Adrian Cockroft

If you have to know too much about surrounding services, you don't have a bounded context. A service is authority of a set of business capabilities.

### Coupling and Cohesion

Yin and yang of software design.

#### Coupling

Afferent Coupling (Ca) - who depends on you?
Efferent Coupling (Ce) - who do you depend on?

![Afferent and Efferent Coupling](https://i.imgur.com/a3SD9wJ.png)

Synchronous Request Response via HTTP doesn't reduce coupling as a monolith. It is the same.

Loose Coupling is a system in which each of its components has or makes use of little or no knowledge of the definitions of separate components. This can be done via a message or event driven architecture.

### Architecture

The main difference is with synchronous request/response, you know WHO cares about it. With event driven architectures, you have no clue who cares about it (Billing, Warehouse, Shipping, etc).

Microservices are a set of events, capabilities, and the data behind it.
