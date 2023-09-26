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



