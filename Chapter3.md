# Chapter 3 - SRE Basic Concepts
The basic concepts of SRE are not numerous and not difficult to explain, which makes this a good starting point for our SRE transformation journey. The concepts are service level indicators, service level objectives, error budgets, and error budget policies.

### 3.1 Service Level Indicators (SLI)
Service level indicators (SLIs) are a foundational concept in SRE. All the other concepts build on top of SLIs. An SLI is succinctly defined as "a service level indicator - a carefully quantitative measure of some ascpet of the level of services that is provided". 

Relavant SLIs for a service are a mmatter of definition. Typical SLIs include availability, latency, and throughput. Determining SLIs is an empirical process based on "intuition, experience, and an understanding of what users want to define service level indicators. 

- Avaliability and latency SLIs are applicable to all services. 

> Key Point: SLIs need to be determined based on customers' perception of reliability, not developers or operations engineers' perceptions. 

On top of the availability and latency SLIs in the heirarchy of reliability are the throughput and coverage SLIs. Throughput can mean the nuber of requests the service processes per time unit or it can ean the amount of data processed per time unit. 

- Not every service needs a throughput SLI

The coverage SLI is also only applicable to certain services. It measures whether a dataset under processing by a service has been processed in full. 

Correctness and fidelity comprise another set of SLIs selectively applicable to services based on their business and technical domains. Correctness is about verifying whether the processing did what it was supposed to do. Fidelity is about the feature fidelity available to users: Are all the features available to users as expected, or are some features switched off for some time because of failure in a system part? In other words, the service may still be available, but the feature set offered to customers may be degraded for some time.

The fresheness and durability SLIs are also applicable to some services, but not all.

- Freshness is about the degree to which the data being servied for processing is the latest data available. (Integrity)
- Durability is about measuring whether the data stored in a data store can be retrieved later on (Availabilty)

> Key Point: This ties into a theory from security called the CIA Triade (Confidentiality, Integrity, Availability), tying freshness and durability to the I and A. 

To reiterate, the SLIs selected to express service reliability need to be chosen from the cus- tomer point of view. The goal is to be able to use the SLIs as proxy measurements of reliability as experienced by customers. The technical experience of the system under strain is not what SLIs are supposed to measure. Rather, the customer experience of the system is what SLIs are supposed to express.

### 3.2 Service Level Objectives 
Whereas SLIs are about customer experience/expectations, SLOs are about how those expectations will be met. 
- SLO is defined as "a target value or range of values for a service level that is measured by an SLI"

Example of Availability: 
- 98% availability of a particular endpoint within period of four calendar weeks
- 99.99% availability of another endpoint within a period of four calendar weeks

Example of Latency:
- 400-millisecond latency for 95% of requests to an endpoint within a period of four calendar weeks
- 250-millisecond latency for 90% of requests to an endpoint within a period of four calendar weeks 

An SLI is measured; for example, availability or latency. An SLO is the measurement threshold that the service should not break. 

The SLO for an SLI has to be set from the customer perspective. Also, and this is hugely important, in order to set the SLO from the customer perspective, a clear definition of the cus- tomer to optimize for is required. Without a clear definition of the customer, an SLO cannot be optimized to reflect the expectations of that particular customer group. Therefore, the SLO will be just a technical measurement that does not reflect the experience of the customer group.

A broken SLO such as this will not reflect a broken customer experience. As a result, once the SLO breach is reported, it will not be clear whether engineering time should be spent fixing the service to bring it back within the SLO.

### Error Budgets 

An error budget is a peculiar concept. In software development the goal is to avoid errors. If the software has errors, or bugs, they need to be fixed. An error budget give develops a budget for errors, which seems counterintuitive: If developers are given a budget for errors, there would be even more bugs in production. Should the error budget be zero? 

Remember: An SLO of an SLI is a service level defined to reflect customer happiness. If a service endpoint is within its SLO, the customers are happy. If a service endpoint does not meet its SLO, the customers are not happy and start complaining about the service. The SLO dictates the error budget that is available to the individual teams. The error budget is the difference between the maximum service level and the SLO. 

> Key Insight: error budget = maximum service level - SLO threshold

The error budget is the difference between the maximum service level of 100 and the SLO threshold. Much like a monetary budget, the error budget is allocated per time unit. This means the service endpoint may deplete the error budget within the time unit but should not exhaust it before the time unit ends! That is, staying within the error budget means not exhausting it within the given time unit.

The goal being to not prematurely deplete the error budget before the end of each time unit. The error budget does not roll forward, however can be utilized on a 28 day rolling time unit or sliding window. 

#### 3.3.1 Availability Error Budget Example
See Chapter 3, Figure 3.7 for illustration and example

#### 3.3.2 Error Budget of Zero
If the error budget is set to zero this means the service is always available and would have an SLO set to 100%. Even though the SLO is set to 100% this does not mean the service will have 100% availability. This is because the service is deployed somewhere, and the service consumers are deployed somewhere else. Between the service and the service consumers is a network that consists of many network gear devices, cables, and is dynamic in terms of packet routing. Any of these network components may fail. In the case of a network failure, the service consumers will not experience the service as being 100% available on their end, even if the service itself is 100% available where it is deployed.

Even if the network is not taken into account for the time being and only the point of deploy- ment is considered, can the SLO of 100% availability be met? If so, what would that require? An availability SLO of 100% means the corresponding error budget is 0%. There is no room for errors. All requests to a service endpoint with a 100% availability SLO have to succeed within a given time unit. This, in turn, means the team developing and operating the service must do eve- rything they can to meet the SLO and error budget. 

- See Chapter 3, Table 3.2 for examples 

Without an error budget in place, the development team starts acting like a traditional opera- tions team. The traditional operations team did not want any changes in production. “Never touch a running system” is a well-known slogan in the software industry. However, not touching the system leads to the system becoming irrelevant to customers. Becoming irrelevant and losing customers and revenue is not a sign of a successful product.

> Key Point: Defining an availability SLO of 100% that leaves no error budget whatsoever con- tradicts the purpose of making the product successful.

Defining any SLO of 100% for any SLI leaves zero error budget. This contradicts the purpose of making the service, the prodcut, and the business successful. 

> Key Insight: An SLO of 100% leaves an error budget of zero. With an error budget of zero, developers do not want to update the service in production, because doing so might lead to an outage. Every outage chips away at the error budget, which is not available in this case. Not updating the service leads to stagnation and irrelevance of the service to customers. That is, an error budget of zero contradicts the purpose of making the service and the product successful.

This is not to say that a service endpoint cannot run without depleting any error budget within a given time unit. Great serrvices often run without depleting any error budget within a given time unit. However, the SLOs of those services are not set to 100%, leaving no eror budget available. Having no error budget avaialable right from the start would make the develpment team freeze and not want ot achieve the following two gaols: 

1. Implement features that are actually used by customer on a regular basis
2. Roll out the features and operate tehm without exhausting the error budget prematurely

For the serviec to be successful, these two goals must be met simultaneously. In order to motivate the teams to achieve these goals, they need room (error budget) to operate. This is done by setting the SLO to a value sub 100%. 

#### 3.3.3 Latency Error Budget Example 
Refer to Chapter 3, Figure 3.8 for details

- Latency error budget = 100% of requests – 95% of requests within 400 milliseconds =
5% of requests without the 400-millisecond return time cap

The error budget is granted for four calendar weeks. Therefore, the goal of the team developing and operating the service is not to exhaust the error budget prematurely, before the end of a given period of four calendar weeks.

Equipped with a good understanding of error budgets, the next SRE concept to explore is that of error budget policies.

### 3.4 Error Budget Policies 
An error budget policy, in its simplest form, is a policy that states what the team developing and operating the services will do to improve reliability when a service exhausts its error budget pre- maturely. In this context, prematurely means before the end of the time unit for which the error budget was granted. Premature error budget exhaustion can easily happen when planned or unplanned incidents with the service lead to so much error budget depletion that there is no error budget left before the end of the current time unit.

Each time the respective SLO is broken, a tiny bit of the error budget is depleted. The more frequently the SLO is broken, the more frequently the error budget is depleted.

A good alert from the SRE infrastructure states the origin of the SLO breach and the remaining error budget in the given time unit. Based on this information, the people who are on call receiving the alert can quickly assess the priority to be assigned to the alert.

In terms of error budget debt handling, unlike money debt, error budget debt does not accumulate. Rather, the SRE infrastructure provides full error budget debt relief at the beginning of each time unit. However, error budget debt is paid by the service customers. Error budget debt indicates that the customer experience is severely impacted, which may have monetary conse- quences. The customers may decide to vote with their feet and leave a service that is unreliable.

This is where the error budget policy comes in. In its simplest form, it states an agreement among the operations engineers, developers, and product owner about what the team will do when the error budget is used up prematurely. An error budget policy may contain items such as the following.

- The team will conduct a blameless retrospective to understand teh reasons for the premature error budget depletion or exhaustion
- The team will stop deploying new features to production and only deploy technical reliability improvements until the service is back within its SLO steadily for a period of time
- The team will review the implementation, architecture, and dependancies of the service to derive reliability measures to be taken. 
- The team will assess whether a regulatory notice needs to be submitted to the regulatory bodies to report the service reliability levels and consequences thereof. 
- Until the service is steadily within its SLO for a period of time, the team will stop performing production deployments, overriding deployment tool warnings about low levels of error budget that remain available. 

Error budget policy is a team-based agreement by the team members applicable to all servies owned by the team. 

### 3.5 SRE Concept Pyramid
Refer to Chapter 3, Figure 3.10 for illustration

### 3.6 Alignment Using the SRE Concept Pyramid 
How do the individual SRE concepts play together to align the product delivery organization with streamlined product operations? Fundamentally, the concepts support the organization to create the alignment before actual production deployment. Going into production deployment as an aligned organization is the key to great product operations. So, what needs to be agreed to before production deployment, and by whom?

- Refer to Chapter 3, Figure 3.12 for answers to the above questions 

The SLO definition agreed to by the developers, operations engineers, and product owner is a collective attempt to find the SLO magic line that would balance customer happiness with the engineering effort required to achieve it. The SLO magic line is a hypothesis at this point

Test the hypothesis. This is done by letting the SRE infrastructure moni- tor production for the fulfillment of the defined SLO. Should the SLO be broken, the SRE infrastructure notifies the people on call. They need to analyze the SLO breaches and find out whether they reflect a severely impacted customer experience. If the SLO breaches do not reflect a severely impacted customer experience, the SLO needs to be redefined. The redefinition can now be done with the benefit of having real data and insight from production. It should go with- out saying that the SLO redefinition needs to be done and agreed to by the operations engineers, developers, and product owner.

