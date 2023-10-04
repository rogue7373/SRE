# Chapter 11 - Enabling Error Budget-Based Decision-Making
Error budget–based decision–making is the topmost concept in the SRE concept pyramid (see Section 3.5). It rests on all the other concepts beneath: error budget policies, SLOs, and SLIs. Ena- bling error budget–based decision–making puts a product delivery organization in a true position to steer reliability efforts on many levels in a data-driven way. With that, which reliability decisions can be driven by error budget–based decision–making? The answer to this question is very wide ranging. 

### 11.1 Reliability Decision-Making Taxonomy 
The following decision categories can be supported by error budget–based decision–making in the realm of reliability:

- Prioritization decisions
- Development decisions
- Deployment decisions 
- Converstation decisions
- Test decisions
- Requirement decisions
- Budget decisions
- Legal decisions 

- Decision Categories Supported By Error Budget-Based-Decision-Making

| Decision Category | Decision Examples and Associated Questions | 
|----|----|
| Prioritization | Decision to enact the error budget policy: <ul><li> Have the error budget policy conditions in terms of error budget depletion been met?</li></ul>Decisions to adapt the error budget policy<ul><li>Does enactment of the error budget policy entail error budget depletion that leads to an unsatisfactory reliability user experience</li><li>Does the error budget policy get enacted too late for error budget depletion to be within the scope of a satisfactory reliability user experience?</li></ul>Decisions to prioritize services in most of reliabiltiy improvements:<ul><li>Which services consistently exhausted their error budgets prematurely across all SLIs in the last three error budget periods</li><li>Which services exhausted their availability error budgets prematurely in the last three error budget periods</li><li>Which services exhausted their latency error budgets prematurely in the last three error budget periods?</li><li>What are the most critial SLIs by service?</li><li>Which services are teh fasted premature error budget exhausters by SLI in the last three error budget periods?</li><li>Is the service customer facing</li></ul> |
| Development | Decisions to consume an API: <ul><li>What is the defined reliability of the API?</li><li>What are the defined SLOs for the API?</li><li>What are the defined SLAs for the API?</li><li>Are the defined SLOs and SLAs sufficient to provide a good user experience for the use cases intended to be implemented?</li><li>What is the historical adherence to the defined SLOs and SLAs in the target deployment environments?</li></ul>Decision to implement adaptive capacity between services: <ul><li>What is the adherence to the defined SLOs over time in the taget environment exhibited by the service considered to be consumed</li></ul>Decision to check whether implemented reliability improvements have led to reduced error budget depltion:<ul><li>Did the error budget depletion of a service reduce in the error budget period after the implemented reliability improvement compared to previous periods?</li></ul> |
| Deployment | Decision about denying a production deployment: <ul><li>Does a service’s error budget depletion pattern correspond to an error budget policy condition with the consequence of denying production deployments?</li></ul>Decision about denying a deployment into a nonproduction environment: <ul><li> Are SLO sets defined as entry criteria for allowing new deployments into a nonproduction environment?</li></ul> |
| Conversation | Decision to talk to a team owning a dependent service to get the SLOs of the dependent servbice tightened: <ul><li>Does a new customer use case resulting in a new interaction between a team's service and a depenedent service require tighter SLOs for the dependent service?</li></ul> | 