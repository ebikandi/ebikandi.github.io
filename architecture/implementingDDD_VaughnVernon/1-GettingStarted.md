# Chapter 1: Getting started with DDD

# Can I DDD?

- ***Software model:\*** the way the software expresses the solution to the business goal being sought.

Even if we could produce completely bug-free software, that in itself does not necessarily mean that a quality software model is designed, the software-model could still suffer greatly. DDD helps us reach the point where our design is exactly how the software works.

If you are capable of understanding **the business in which your company works**, you can at a minimum participate in the **software model discovery process to produce a \*Ubiquitous Language\*.**

- ***Domain experts:\*** The people who know the line of business you are working in really well.

Engage with domain experts. Learn from them and let them learn from you.

- ***Domain model:\*** These are the people who know the line of business you are working in really well. With DDD your domain models will tend to be smallish, very focused. Using DDD, you never try to model the whole business enterprise with a single, large domain model.

# Why you should do DDD?

- Make a cohesive team formed by experts and developers.
- Make software that is closest as possible to the bussines.
- Everybody learns because everybody contributes.
- Everybody knows.
- Develop a common language that can be used by experts and developers.
- The design is the code, and the code is the design.
- Helps us understand what are the most important software investments to make (**Stratetic Design**)
- Helps us craft the single elegant model of a solution using time-tested, proven software building blocks (**Tactical Design**).

## Delivering Business Value Can Be Elusive

Software that is not about technology, but about the business.

Business knowledge is never centralized. One of the worst disconnects of a business software development effort is seen in the gap between domain experts and software developers.

**A different, yet related problem is when one or more domain experts do not agree with each other. Worse still is when the technical approach to software development actually wrongly changes the way the business functions**.

- Eg. change the overall business operations of an organization to fit the way the ERP functions.

## How DDD Helps

- Brings domain experts and software developers together in order to develop software that reflects the mental model of the business experts. Develop an **Ubiquitous Language** spreading deep domain insight among all team members.
- It helps define the best inter-team organizational relationships and provides early-warning systems for recognizing when a given relationship could cause software and even project failure.
- Meets the real technical demands of the software by using tactical design modeling tools to analyze and develop the executable software deliverables.

## Grappling with the Complexity of Your Domain

We primarily want to use DDD in the areas that are most important to the business. You invest in the nontrivial, the more complex stuff, the most valuable and important stuff that promises to return the greatest dividends (**Core Domain**).

- [Core, Supporting and Generic Domains](https://blog.jonathanoliver.com/ddd-strategic-design-core-supporting-and-generic-subdomains/)

> Use DDD to model a complex domain in the simplest possible way. **Never use DDD to make your solution more complex**. Thus, your team and management will have to determine if a system you are planning to work on **deserves** the cost of making a DDD investment.

[When we shouldn't use DDD? in stack-overflow](https://stackoverflow.com/questions/27638513/when-we-shouldnt-use-domain-driven-design-approach)

## Anemia and Memory Loss

- Anemic Domain Model:

   A domain model that is weak, without the power of inherent behavioral qualities.

  - Only have gettes and setters, bussiness logic in components using these getters, ...

An Anemic Domain Model is a bad thing because you pay most of the high cost of developing a domain model, but you get little or none of the benefit

## Reasons Why Anemia Happens

- Copy-pasted or oversimplified code anywhere.
- SRP rule broken. Functions doing a lot of stuff far from their original intention.

# How to do DDD

- **Ubiquitous Language:** A shared team language, domain experts and developers alike. How we can achieve this?

  - Draw pictures of the physical and conceptual domain and label them with names and actions.
  - Create a glossary or documentation of terms with simple definitions. **And review them with all the team.**

  These first traces of Ubiquitous Language will very likely be rendered obsolete over time. That’s why in the end it is team speech and the model in the code that are the most endur- ing and the only guaranteed current denotations of the Ubiquitous Language.

  When implementing DDD, **questioning the design is expected**.

  .The **Application Service would also be refactored to reflect the explicit intentions** of the business goals at hand. Each Application Service method would be modified to deal with a single use case flow or user story.

## Ubiquitous, but Not Universal

A few basic concepts:

- Is spoken among the team and expressed by the single domain model.
- Is not an attempt to describe some kind of enterprise-wide, company-wide, or worldwide, universal domain language.
- One Ubiquitous Language per Bounded Context**.**
- A Bounded Context is large enough only to capture the complete Ubiquitous Language of the isolated business domain, and no larger**.**
- The Language is ubiquitous only within the team that is working on the project that develops in an isolated Bounded Context.
- There are always one or more additional isolated Bounded Contexts with which it integrates using **Context Maps**. Each of the multiple Bounded Contexts that integrate has its own Ubiquitous Language, even though some terms of each may overlap.
- If you try to apply a single Ubiquitous Language to an entire enterprise, or worse, universally among many enterprises, you will fail. Each BoundedContext will have its language and two different terms in two different Bounded Contexts (thus, languages) can mean the same. Hence, there can be a mapping framework which will point that tem1 and term2 are synonims.

**Identify the isolated Bounded Context** that is being developed. This places an explicit boundary around your domain model. Reject all concepts that are not part of the agreed-upon Ubiquitous Language of your isolated Context.

# The business value of using DDD

Software developers can no longer pursue technologies and techniques just because they sound cool or intriguing. We must justify everything that we do. The best justifica- tion for using any technology or technique is to **provide value to the business.**

### A useful model of its domain

**Focus on the Core Domain**. Other models exist to support the Core Domain and are important, too. Yet the supporting mod- els may not be given the priority and effort of the Core Domain

When our focus is on what distinguishes our business from all others, our mission is well understood and we will deliver exactly what is needed to achieve competitive advantage.

### A refined, precise definition and understanding of the business is developed

The business may actually come to understand itself and its mission better than before. As the model is refined over time, the business develops a deep understand- ing that can serve as an analysis tool.

### Domain experts contribute to software design

Domain experts don’t always agree on concepts and terminology.he organization grows a deeper understanding. Yet when brought together to a DDD effort, the domain experts gain consensus among themselves.

Developers now share a **common Language** as a unified team along with domain experts, thus, training and handoffs are easier.

### A better user experience

When the user experience is designed to follow the contours of the underlying expert model, users are **led to correct conclusions**.

### Clean boundaries are placed around pure models

The technical team is discouraged from doing what might appeal more to their programming and algorithmic interests by **aligning expectations with business advantage**.

### Enterprise architecture is better organized

The boundaries are explicit, so the team develops an acute understanding of **where and why integrations are necessary.**

### Agile, iterative, continuous modeling

The model that is produced is the working software. It is refined **continuously** until it is no longer needed by the business.

### Strategic and tactical tools are employed

A Bounded Context gives the team a modeling boundary in which to create a solution to a specific business problem domain. Within a single modeling boundary the team may employ any number of useful tactical modeling tools: **Aggregates, Entities, Value Objects, Services, Domain Events**, and others.

# The Challenges of Applying DDD

- Allowing for the time and effort required to **create a Ubiquitous Language**.
- **Involving domain experts** at the outset and continuously with the project.
- Changing the way developers **think about solutions** in their domain.

When you do get the domain experts’ involvement, the onus falls back on the developers. **Developers must converse with and listen carefully to the true experts**, molding their spoken language into software that reflects their mental model of the domain.

What an object does by means of a specific behavior must be considered. It’s about d***esigning the behaviors of objects***.

### ❌ client commits the backlog item to a sprint by setting its sprintId and status

```jsx
public class BacklogItem extends Entity {
    private SprintId sprintId;
    private BacklogItemStatusType status;
    ...
    public void setSprintId(SprintId sprintId) {
        this.sprintId = sprintId;
}
    public void setStatus(BacklogItemStatusType status) {
        this.status = status;
}
... }

// ❌
backlogItem.setSprintId(sprintId);
backlogItem.setStatus(BacklogItemStatusType.COMMITTED);
```

- The client must know how to correctly commit the backlog item to a sprint.
- The model, which is not really a domain model, doesn’t help at all.
- What if the client mistakenly changes only the sprintId but not the status
- Exposes the shape of the BacklogItem object and clearly focuses attention on its data attributes and not on its behaviors.

### ✅ client commits the backlog item to a sprint by using a domain-specific behavior

```jsx
public class BacklogItem extends Entity {
    private SprintId sprintId;
    private BacklogItemStatusType status;
    ...
    public void commitTo(Sprint aSprint) {
        if (!this.isScheduledForRelease()) {
            throw new IllegalStateException(
                "Must be scheduled for release to commit to sprint.");
}
        if (this.isCommittedToSprint()) {
            if (!aSprint.sprintId().equals(this.sprintId())) {
                this.uncommitFromSprint();
            }
        }
        this.elevateStatusWith(BacklogItemStatus.COMMITTED);
        this.setSprintId(aSprint.sprintId());
        DomainEventPublisher
            .instance()
}
... }

// ✅ 
backlogItem.commitTo(sprint);
```

- Exposes a behavior that **explicitly and clearly indicates that a client may commit a backlog item** **to a sprint**. Thus, captures the Ubiquitous Language.
- Clients don’t need to know what is required to perform the commit.

## Justification for Domain Modeling

*Tactical* *modeling* (delivery) is generally **more complex** than *strategic* *modeling* (development). Thus, if you intend to develop a domain model using the DDD tactical patterns (Aggregates, Services, Value Objects, Events, and so forth), doing so will require more careful thought and greater investment.

Some practical guidance:

- If a Bounded Context is being developed as the Core Domain, it is strategically vital to the success of the business. Will long for a long time, evolve, possibly could be refactored and maybe will not be your Core Domain in the future. This assumes that your Core Domain deserves the best developer resources with a high skill level.
- A domain that may become a **Generic/Supporting  Subdomain** to its consumers may actually be a Core Domain to your business.
- If the team is capable of properly applying tactical design, and the Supporting Subdomain is innovative and must endure for years in the future, this is a good opportunity to invest in your software using tactical design.

The type of business domain itself is not automatically the determining factor for choosing a development approach. Your team should consider import- ant questions to help you make the final determination:

- Are domain experts available and are you committed to forming a team around them?
- Although the specific business domain is somewhat simple now, will it grow in complexity over time? Will the potential for refactoring to a behavioral domain model later on be practi- cal if/when the Context becomes complex?
- Will the use of the DDD tactical patterns make it easier and more prac- tical to integrate with other Bounded Contexts?
- Transaction ScriptWill development really be simpler and require less code if you use [Transaction Script](https://dzone.com/articles/transaction-script-pattern)?
- Do the critical path and timeline allow for any overhead required for tactical investment?
- Will the tactical investment in a Core Domain protect the system from changing architectural influences?
- Will clients/customers benefit from a cleaner, enduring design and devel- opment approach, or **could their application be replaced by an off-the-shelf solution tomorrow**?
- Will developing an application/service using tactical DDD be more difficult?
- If the team’s toolkit was complete with DDD enablers, would we conscientiously choose to use another approach instead?

### DDD Is Not Heavy

It is meant to fit well into any **agile** project framework, such as Scrum, that the team desires to use. An example of the steps to take to develop a new Value Object:

1. **Write a tes**t that demonstrates how the new domain object should be used by a client of the domain model.
2. **Create the new domain object** with enough code to make the test compile
3. **Refactor** both until the test properly represents the way a client would use the domain object.
4. **Implement** each domain object behavior **until the test passes.**
5. Demonstrate the code to team members, including domain experts. (Check *Ubiquitous Language*)

# Fiction, with Bucketfuls of Reality

Sometimes it’s easier to look at the problems faced by other project teams and **learn from their misuse** of DDD than it is to look inward. Knowing where you are headed or where you already are, you can make the precise adjustments to correct problems and avoid the same in the future**.**