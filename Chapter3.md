# Chapter 3 - SRE Basic Concepts
The basic concepts of SRE are not numerous and not difficult to explain, which makes this a good starting point for our SRE transformation journey. The concepts are service level indicators, service level objectives, error budgets, and error budget policies.

### 3.1 Service Level Indicators (SLI)
Service level indicators (SLIs) are a foundational concept in SRE. All the other concepts build on top of SLIs. An SLI is succinctly defined as "a service level indicator - a carefully quantitative measure of some ascpet of the level of services that is provided". 

Relavant SLIs for a service are a mmatter of definition. Typical SLIs include availability, latency, and throughput. Determining SLIs is an empirical process based on "intuition, experience, and an understanding of what users want to define service level indicators. 

- Avaliability and latency SLIs are applicable to all services. 

> Key Point: SLIs need to be determined based on customers' perception of reliability, not developers or operations engineers' perceptions. 

