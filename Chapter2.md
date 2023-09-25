# Establishing SRE Foundations - A Step-By-Step Guide to Introducing Site Reliability Engineering in Software Delivery Organizations

## Chapter 2 - The Challenge
Users touch the product in productions, therefore, that touch point needs to be centric with all activities in the product creation life cycle. 

#### Example from the book
> The consequence of not thinking about production throughout the product creation life cycle can be illustrated using an example from the grocery industry. Imagine that a grocery store chain has a wide variety of products displayed in beautifully designed stores throughout the country, but neglects the checkout counters at the point of sale. The entire supply chain is working flawlessly, but issues arise at the checkout where the customers are trying to purchase their groceries: for example, they might not be able to pay for their groceries quickly, and the checkout queues might be getting longer. The checkout staff might not be able to resolve the issues themselves. The point-of-sale devices are supported by the operations team, which receives an enormous number of support requests. It turns out that the issues are with the software on the devices; the support team cannot resolve the software issues themselves.

> While the crisis is unfolding, the developers are happily working on new features for the point- of-sale devices. The product owners are happily specifying additional new features to be handed over to the developers after they finish the current work. The operations engineers are reaching out to the developers, who are not sure whether to prioritize the requests by the operations engineers or the features in development. The developers reach out to the product owners for a prioritization decision. Finally, the operations engineers, developers, and product owners swarm over the problem and decide to fix the product issues with the highest priority.

### 2.1 Misalignment 
* See Figure 2.1 which illustrates the preceding example of how a product delivery organization misaligned on operationsal concerns works. 

If productions is where the customers use the product, how on earth can it be less important than anything else? 

This frustration relfects a core issue in product delivery organizations that do not excel at operations. In such organizations, being product and user centric means different things to different parties. From a product operations point of view, it means produciton isses are tackled with the highest priority. From a product development point of view, it means features reqeusted by product owners are develped as quickly as possilbe. From a product management point of view, it means user stories requested by customers are turned into features in production as quicly as possible. This fundamental misalignment of what it means to be product and user centric when approaching product creation is one of the core reasons for difficulties in operating the product in production to the customer's satisfaction. This is where SRE shines, aligning the parties (Chapter 1, SRE brings together the three parties)

The three parties operate under three different flags

1. Product Operations runs under the Ops flag - they man production
2. Product Development runs under the Dev flag - they develop products new features
3. Product Management runs under the Product flag - they are all about the product and shape it in a fundamental way: What is it? Who are the customers? What is the competition? What is the product’s competitive advantage? What are the most important user journeys? What are the features? What is on the backlog?

It turns out that in a setup like this, no one really owns production operations. Who is it, indeed? Is it product operations? Not really, because they lack the knowledge necessary to truly own production operations. There is no proper continuous knowledge transfer from product development and product management toward product operations, and vice versa.

Is it product development? Certainly not. Their focus is the feature backlog. The feature backlog is void of product operations. Shipping occasional necessary production hotfixes after escalations from product operations is not what owning production operations actually means.

Is it product management? For sure it is not. Their focus is the definition of the product. Their expectation is that product development implements the product and product operations operates it in production. Despite the word owner in their title, the product owners do not own the product all the way to and including production.

### 2.2 Collective Ownership
Collective ownership is the ownership of means of production by all members of a group for the benefit of all its members. The definition shows that everyone needs to benefit from the ownership. In the context of product operations, it means that if collective ownership is to be established ina product delivery organization, the ownership needs to benefit all the parties involved. If collective ownership of productions operations is to be established among product operations, product development, and product managmentment, each party needs to benefit from it. 

Product operations team struggle to engaged product development and product management teams in their operations activities. It is preferred that PM and PD take partial ownership of operations. 

PD teams view themselves as feature developers with the goal of getting new features to production quickly
Collective ownership is the ownership of means of production by all members of a group for the benefit of all its members. The definition shows that everyone needs to benefit from the ownership. In the context of product operations, it means that if collective ownership is to be established ina product delivery organization, the ownership needs to benefit all the parties involved. If collective ownership of productions operations is to be established among product operations, product development, and product managmentment, each party needs to benefit from it.

### 2.3 Ownership Using SRE 
What does it mean to have parital ownership of production operations using SRE? This question needs to be answered specifically for each party in the product development organization.

#### 2.3.1 Product Developement
The benefits of partially owning production operations are rooted in the insights of how the system behaves in production under real user, data, and infrastructure load. 
- We observe in production - this helps to continuously learn about our systems in the real world environment
- We use on-call rotations, typically handled by product operations, this way production insights don't go directly to production development 
- The helps to prevent masking of issues
- Developers with product implementation knowledge conduct product failure investigations
- The number of steps in the chain between a production issue occurring and a person with
the best knowledge to fix it can be exactly one. (Only acheivable via active, actionalble alerting)
- Developers get to experience the quality of the product in the real world by testing it at productions sites. 
- Developers gain the knowledge necessary to operate and troubleshoot the product. 
- Developers use the knowledge from product operations in the development of new features.
- Developers gain a better understanding of the kind of testing and tooling necessary to deliver a product that works well. 
- Developers have the incentive to implement reliability features and tools for a great product operations experience. This is because if the developers go on call, they actually want to spend as little time as possilbe dealing with production issues. 
- Developers with experience in product operations are more highly valued in the industry. Going on call directly contributes to learning the skills necessary to command higher wages in the marketplace (Learn Operations before development to earn more $$$)

The idea of going on call for the developers gives rise to a plethora of questions, such as the following: 

- Do the developers always need to go on call for their services? No
- Could the developers go on call only during business hours? Yes
- Can the on-call responsibility be shared with product operations? Yes
- What is the best setup for given organizatinos? No right answer
- Would a development team setup need to be adapted to enable on call? Yes
- Can developers in a team perfomr the on-call duties on rotation? Yes
- Can focused feature development still be done despite going on call? Yes
- How do you achieve it? Again, no right answer, find what fits
- Can developers stay developers if they go on call? Yes. They will become better developers and their skills will be more highly sought after. 

The book will further discuss the above in upcoming chapters, if you have questions I suggest writing them down as they will be answered going forward.

> Key Insight: Developers must go on call for some percentage of their time. This can range from very little time to nearly full time. (Finding a balance for your personal organization is up to you. What works for some might not work for everyone.)

#### 2.3.2 Product Opertations
With developers going on call, the product operations team would need to provide support to enable the developers to do operations. 

What kind of support would the developers need? Some developers may have never done operations before, so this may be unfamiliar to them. 

The entire body of knowledge about product operations is with the operations team. The idea of taking product as a "black box" and putting it into thep production environment, activating monitoring of IT resources, and alerting on some threshold violations. This allows developers to learn and understand this. With thier insider knowledge of the produc, they will also be able to find many more scenarios that can be monitored and alerted upon.  The developers’ knowledge about the architecture, implementation, configuration, and deployment of the product is an invaluable resource for improving monitoring of the product in production. But how can they utilize that knowledge to improve product operations?
How can they bridge the gap between development and operations as suggested by the term
DevOps?

Developers know how specific routines that contribute to the fulfillment of user requests are implemented. They know the paths the user requests go all the way from the user interface to the deepest service in the service network, and from there to the infrastructure. If the product exposes APIs to customers, the developers also know the paths the API requests take from the API gateway through the network of services all the way down to the infrastructure. Moreover, the developers know which services they imple- mented versus those implemented by the company and third parties. They know which third- party services are difficult to integrate with, where the domain model of the third-party services is overly complicated and cluttered, where the third-party services are slow occasionally, and where there is simply sporadic behavior that can be explained. The developers also know all this for the internal services of the company, which are the services they depend upon.

Their knowledge does not stop there. The developers and architects know the strengths and weaknesses of their architecture. They know where the architecture limitations lead to perfor- mance and scalability issues. They know the circumstances where the performance and scalabil- ity issues are likely to exhibit and probably impact the customer. They know the architectural debt in the system and which part of it is planned to be paid off in the near future. They know of any major architectural refactorings that must take place, which are not planned due to the size of the effort involved.

The developers’ knowledge goes much further. They know about the infrastructure limita- tions the product is running on. They know how each service can impact the others; for exam- ple, they know what will happen if a particular service in the service network eats up the lion’s share of memory in a given area of the infrastructure. They might know some parameters of the container clusters the services are running in and anticipate issues that might occur based on the changing data and user load profiles.

They may know the way the services are deployed: Which infrastructure parameters are set by the deployment infrastructure, and which ones are set in the service at the deployment time, startup time, or runtime. They know which ser- vices are deployed independently, which ones use a shared deployment pipeline, and which ones are deployed manually for the time being. They may know the tests running on the deployment pipelines, the quality of those tests, and whether the test results can be trusted. They may know the test management process for a service, the test levels available, the test infrastructure, and any test gaps that exist.

The developers also likley know security inforation surrounding their domain, whether that be due to architecture or infrastructure. 

This is where operations sees a gap, while the developers may have this wealth of knowledge, the amount of knowledge the developers have is staggering to the operations engineers. How do they take it all in? 

To approach these questions, we need to turn our attention to how developers make known to the outside world what is going on with the system on the inside.

- This is done using logging.

The log entries stored in, for example, log files or other storage systems can then be analyzed to understand what was going on in the system at runtime. This is the basic process of how devel- opers make known to the outside world what is going on inside a system at runtime. The process is sophisticatedly supported by tools providing all sorts of runtime instrumentation out of the box. That is, the developers’ knowledge about the product can be encoded in logs that can be analyzed outside the system.

Once that question has been answered, we can then consider how to log relavant information in a uniform way. Determining log formats, storage locations, etc. 

From there, you determine how to detect "abnormal situations", what is considered "broken". Once you have determined what is "abnormal" you determine how you want to alert on the abnormalcies. The list of questions only grows from there. 

* Key Insight: Operations engineers need to provide frameworks to enable developers to do service opertations. In a SRE context, such a framework can be referred to as SRE infrastructure. 

The following unfolds as a challenge in the SRE transformation: 
- Software developers need to learn how to do product operations work by going on-call. 
- Operations engineers need to learn how to enable software developers to do operations work by developing the SRE infrastructre as a framework.

#### 2.3.3 Product Management

