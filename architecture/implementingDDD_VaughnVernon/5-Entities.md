# Chapter 5: Entities



## Why we use Entities?

- An Entity is a **unique thing** and is capable of **being changed continuously** over a long period of time.
- We may be interested in **tracking when, how, and by whom** changes were made.
  - It is the unique identity and mutability characteristics that set Entities apart from **Value Objects**.
- Sometimes modeling entitties and such is not worth it, and a CRUD-based solution can be the beste choice for saving time and money, but sometimes developing a big complex CRUD can be expensive too. 
  - Taking the best choice is key. If DDD is a **justifiable** investment in the business’s bottom line, we use Entities as intended.
- When an object is **distinguished by its identity**, rather than its attributes, make this primary to its definition in the model.

## Unique Identity

- On early Entity defining stages, **focus only on those primary attributes and behaviors** that are central to its unique identity.
  - Focus on attrs. and behaviour that identify it or are commonly used to find or match it. Add only behavior that is essential to the concept and attributes that are required by that behavior.
  - Use UUID as id for distinguishing different entity instances.
- **Value Objects** can serve as <u>holders of unique identity</u>. They are <u>immutable</u>, which ensures identity stability, and <u>any behavior specific to the kind of identity is centralized</u>. Different strategies to provide unique identity:

### User Provides Identity

- Identity built using inputs types by the user in a form.
- Works best **when human-readable identity is a must**.
- We can't rely on users to input correct non-unique identifiers, but we can use the data to build those. Anyway, **adding a few extra cycles to ensure the quality** of the identity is a good investment.

### **Application Generates Identity**

- **Care must be taken when the application is clustered or otherwise distributed** across multiple computing nodes.
- Identity creation patterns:
  - *universally unique identifier* (UUID)
  - *globally unique identifier* (GUID)

> **Local identity** means that Entities held inside an Aggregate need only have uniqueness among other Entities held inside the same Aggregate

- We currently **use this approach** in our projects:

  1. App. layer (e.g *useStartOrder* hook) creates a uuid based id.
  2. A creation command (e.g *StartOrder*) is dispatched with all the needed data (inluding the id)
  3. The data is persisted in the DDBB and finnally, a domain event (s.g *OrderStarted*) is published with the created id. 

  That way, all the flow knows the id, and the creation <u>command does not need to return the created Id</u> (**<u>ANTIPATTERN</u>**! Command don't return anything)

### Persistence Mechanism Generates Identity

- Delegating the generation of unique identity to a persistence mechanism has some unique advantages, because if we relay on a DDBB to generate ids, incrementing the last one, it'll always be unique.

### Another Bounded Context Assigns Identity

- When another Bounded Context assigns identity, we need to integrate to find, match, and assign each identity
- Synchronization can be mad eusing Domain Events.
  - This is rarely easy to do, but it leads to more autonomous systems

### When the Timing of Identity Generation Matters

- Beware of race-condition or multiple entity creations to make sure you're creating/using the right identities.

### Surrogate Identity

- When you need a identity for the domain, but another one for the ORM/framweork.
  - The last one would be the <u>surrogated identit</u>y.
- Can be solved creating a new attribute/column in the entity/table to store that surrogated identity.
- It’s best to hide the surrogate attribute from the outside world. Because the surrogate is not part of the domain model,

### Identity Stability

- Protect unique identity from modifications.
  - Hide identity setters from clients and create guards.

## Discovering Entities and Their Intrinsic Characteristics



