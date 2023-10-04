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
| Reliability | Decisions to set SLOs for a team's service: <ul><li>What are the SLOs and SLAs of internal dependant services?</li><li>What are the SLAs of external dependent services?</li><li>What is the level of adaptive capacity currently implemented between a team's service and dependent services?</li></ul> | 
| Test | Decisions to choose a hypothesis to test using chaos engineering: <ul><li>Which services are the slowest availability error budget depletors?</li><li>Which services did not exhaust the latency error budget prematurely in the last three error budget periods?</li><li>Which services depleted the least availability error budget in the last three error budget periods?</li><li>Which services depleted the least latency error budget in the last three error budget periods?</li><li>Which services have the tightest SLOs defined?</li></ul> |
| Requirement | Decisions to add new BDD scenarios:<ul><li>For which SLIs are the error budgets depleted most by service in the last error budget period?</li><li>Based on the postmortem analyses of the last three budget periods, which new BDD scnearios can be added to test the use cases frequently broken in production in other deployment pipeline environments that precede production?</li></ul> | 
| Budget | Desicions to allocate more SREs to a team: <ul><li>Which team consistently exhausted some of their error budgets prematurely in the last three error budget periods?</li><li>Does the team have an on-call rotation?</li><li>How many people are practiciing SRE in the team?</li><li>What is the 12-month trend of customer support ticket numbers for the serivces owned by the team?</li></ul>Decisions to allocate more SREs to an organizational unit:<ul><li>The same questions as in the previous decision but at the organizational unit level</li></ul>Decisions to allocate a (project) budget for reliability improvements:<ul><li>How many services consistently exhausted some of their error budgets prematurely in the last three error budget periods?</li><li>How many services are showing a growing 12-month trend of customer support ticket numbers?</li></ul>Decision to allocate a business plan cost position for cost of outages:<ul><li>What is the time to recovery trend for a set of services that generate a given amount of revenue per time unit?</li></ul> |
| Legal | Decisions to set SLAs for own services: <ul><li>What are the SLOs set for own services?</li><li>What is the historical adherence to the SLOs set for own services?</li><li>Is there room to tighten the SLAs? Could they be defended?</li><li>What is a reasonable safety margin between the SLOs and SLAs for a given service?</li></ul>Decisions to agree to contractual penalties for breaking SLAs:<ul><li>What is the incident time to detection trend?</li><li>What is the incident time to recovery trend</li><li>What is the potential monthly revenue loss given the current incident number trend and time to recovery trend?</li></ul> |
| Regulatory | Decisions to use SRE data points in regulatory audits:<ul><li>Where are the defined SLIs, SLOs, and SLAs stated by service?</li><li>Who decided on the defined SLIs, SLOs, and SLAs? Where are the decision records signed by all the decision makers?</li><li>Where are the contracts with customers and partners containing the SLAs?</li><li>Where is the data evidencing the fulfillment of the defined SLOs and SLAs?</li><li>Where are the consequences of breaking SLOs and SLAs stated?</li><li>Who decided on the consequences? Where are the decision records signed by all teh decisioin makers?</li><li>How can someone viw the current state of SLO and SLA fulfillment for any service?</li></ul> |

Implementing the SLIs, SLOs, error budgets, and error budget policies at the lower layers of the pyramid is undoubtedly a great and necessary thrust toward reliability in any product delivery organization. At the same time, the full potential of SRE is ignited with error budget–based decision–making at the top of the pyramid. The SRE coaches should therefore encourage teams not to stop the SRE transformation midway up the pyramid. Rather, the teams should climb the pyramid all the way to the top, reaping the full benefits of data-driven reliabil- ity decision-making in the decision categories specified in the table.

### 11.2 Implementing SRE Indicators
The previous section covered the impressive range of decisions that can be made in a data-driven fashion using error budget-based decision-making. Usefully, most of the decisions can be made, or at least supported, using a standard set of SRE indicators. Implementation of the indicators is the subject of the next sections. 

#### 11.2.1 Dimensions of SRE Indicators
The SRE indicators have a common set of dimensions. 

- Dimensions of SRE Indicators 

| Dimension | Explanation |
|----|----|
| SLI | Most SRE indicators need to show data classified by SLI or across a set of SLIs. |
| SLO | Most SRE indicators need to show data classified by SLO or across a set of SLOs. | 
| Error budget period | All SRE indicators need to show data over time. A commonly useful time period is the error budget period. Showing data by error budget period or across error budget periods is beneficial in the SRE context. | 
| Deployment environment | Most SRE indicators need to show data by deployment environment. Sometimes showing data across deployment environments is beneficial as well. Most common environments will be production environments. However, it can aslo be useful to explore preproduction environments using SRE indicators. | 

#### 11.2.2 "SLOs by Service" Indicator
Displaying a list of SLOs by service might be the most pragmatic SRE indicator. Making the list available to everyone in the product delivery organization to be pulled in a self-service manner has many advantages.

1. The transparency of SRE activities increases significantly. 
2. The reliability levels defined by team and service become accessible to everyone. 
3. Decisions to consume a service API can be supported by the list. 
4. Decisions to implement adaptive capacity between services can be supported by the list. 
5. Decisions to set SLOs for own services can be supported by the list. 
6. Decisions to set SLAs for own services can be supported by the list. 
7. The amount of communication between the operations teams owning the SRE infrastructure and the development teams consuming it is reduced. 

#### 11.2.3 SLO adherenece Inidcator
The “SLOs by service” indicator from the previous section references SLO adherence. It is implemented by the SLO adherence indicator, which shows adherence to the SLO by the service over time in the selected deployment environment.

The SLO adherence indicator can support decisions to consume an API and implement a certain level of adaptive capacity when consuming the API. Furthermore, the indicator can support decisions when setting SLOs and SLAs for own services by showing the SLO adherence of dependent services.

#### 11.2.4 SLO Error Budget Depletion Indicator
The SLO error budget depletion indicator shows SLO error budget depletion over time. To be generally useful for a wide range of purposes, the indicator should enable the user to select the service, SLI, SLO, and deployment environment, as well as the time window and time scale. Notably, a 24-hour time window with an hourly time scale is useful for analyzing immediate error budget depletion. A yearly time window with an error budget period time scale is useful for analyzing long-term error budget depletion trends. An error budget time window with a weekly time scale is useful for analyzing the error budget depletion trend in the current error budget period.

- Which services are the slowest availability error budget depletors?
- Which services depleted the least availability error budget in the last three error budget periods? 
- Which services depleted teh least latency error budget in the last three error budget perioids? 

The average and highest error budget depletion speeds for the columns in the table are calculated using dedicated formulae. For example, the speed with which the error budget is depleted can be determined using the following formula:

> Error budget depletion speed = Percentage of error budget depleted / Time span of depletion

Within an SLO error budget period, several incidents can occur. Each incident will have its own error budget depletion speed. In this case, the average error budget depletion speed per error budget period is determined using the following formula:

> Average error budget depletion speed per period = Sum of error budget depletion speed for all incidents in the period / Number of incidents in the period

The highest error budget depletion speed per error budget period is determined using the following formula:

> Highest error budget depletion speed per period = Max error budget depletion speed of all incidents in the period

- Error Budget Depletion Speed Calculations

| Error Budget Period | Incident | Percentage of Error Budget Depleted | Time Span of Depletion in Hours | Error Budget Depletion Speed | 
|----|----|----|----|----|
