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
| 1 | 1 | 70 | 52 | 70/52 = 1.3% per hour |
| 1 | 2 | 50 | 26 | 50/26 = 1.9% per hour |
| 1 | 3 | 25 | 70 | 25/70 = 0.4% per hour |

This makes the error budget periods comparable based on the average error budget depletion speed. The same way financial quarters can be good or bad depending on quarterly financial results, error budget periods can be successful or unsuccessful depending on premature error budget exhaustion or average error budget depletion speed. 

A high error budget depletion speed, such as in incident 2 in Table 11.3, gives evidence of the outage’s large blast radius. A large blast radius gives evidence of the lack of adaptive capacity in the system. With the presence of adaptive capacity, a system can be robust: A fault, error, or failure in one part of the system does not propagate rapidly to other parts of the system; rather, the damage is contained and the partial functionality is preserved, preventing complete failures.

Adaptive capacity can be introduced in the system using so-called stability patterns for distributed systems.

- Fast Versus Slow Error Budget Depletion over Time

| Incident | Percentage of Error Budget Depleted | Time Span of Depletion in Hours | Error Budget Depletion Speed |
|----|----|----|----|
| A | 80 | 2 | 80 / 2 = 40% per hour |
| B | 80 | 336 | 80 / 336 = 0.2% per hour |

Incident A depleted 80% of the error budget within two hours. Incident B also depleted 80% of the error budget but within 336 hours, which corresponds to two weeks or half of a four-week error budget period. Incident A’s error budget depletion speed is 40% per hour. By contrast, incident B’s error budget depletion speed is only 0.2% per hour.

Just by comparing the error budget depletion speeds, it can be said that incident 1 presumably tapped into a system area with a greater lack of adaptive capacity. If the adaptive capacity were there, 80% of the error budget would probably not be depleted within two hours.

#### 11.2.5 Premature SLO Error Budget Exhaustion Indicator
Premature SLO error budget exhaustion is an important indicator of unreliability. The core of SRE decision-making can be done based on knowledge of services and endpoints exhausting SLO error budgets prematurely across error budget periods. It is about data-driven decisions to determine where reliability investments are immediately required and where new feature investments can be made because service reliability is satisfactory. Two types of information visualiza- tion are useful here: a graph for exploratory purposes and a table for focused decision-making. In the next sections, a premature SLO error budget exhaustion graph and a corresponding table are explored.

#### 11.2.6 - 11.2.13
This is all based on a graph provided in the book. You will need to review this portion of the chapter. 

To summarize: 

- 11.2.6 covers "SLAs by Service" Indicators
- 11.2.7 covers SLA Error Budget Depletion Inidcators 
- 11.2.8 covers SLA Adherence Indicators
- 11.2.9 covers Customer Support Ticket Trend Indicator 
- 11.2.10 "On-Call Rotations by Team" Indicators
- 11.2.11 Incident Time to Recover Trend Indicators
- 11.2.12 Least Available Service Endpoints Indicators
- 11.2.13 Slowest Service Endpoints Indicators 

### 11.3 Process Indicators, Not People KPIs 
The SRE indicators need to be treated as the indicators of the reliability engineering process being executed in the organization. They should not be used as key performance indicators (KPIs) for evaluating people. 

> This is important because if they are used to evaluate people, the people are likely to be inclined to tweak the SRE indicator data to be evaluated in favorable terms.

The SRE coaches need to ensure that the leadership team and people managers are aware of this important aspect. Following this, they must make it clear to the entire product delivery organization that the SRE indicators will not be used for people evaluation purposes. Consequently, no one in the product delivery organization should fear that the SRE indicators may be used for performance appraisals. 

Skewing the data shown by the SRE indicators is actually not that difficult. For example: 

- The number of customer tickets per service is subject to the way the tickets are created. 
- The number of SLO breaches is subject to the way the SLOs are set. 
- The time to recovery from incidents is subject to the way the recovery is determined. 

Therefore, like every other process indicator, the SRE indicators are subject to Goodhart’s law: “Any observed statistical regularity will tend to collapse once pressure is placed upon it for control purposes.” The law was later generalized by Marilyn Strathern: “When a measure becomes a target, it ceases to be a good measure.” This happens because people anticipate the adverse consequence of missing the target. Following this, they might be inclined to take action, altering the measures in order to hit the target.

In order to ensure that the people in the product delivery organization do not spend valuable engineering time trying to alter the data, it should be clear to everyone that the SRE indicators do not influence individual careers. In fact, services are owned by teams. Therefore, the SRE indicators need to be owned by the teams. 

Following this, the SRE indicators are a great topic for discussion in team meetings. If the indicators show improvement potential, which will be the case virtually every time they are looked at, ist is the team's job as a whole to discuss, define, and implement the improvements. Finally, it is alos the team's job to use the SRE indicators after the improvements have been implemented to measure whether the envisioned outcomes were indeed acheived. 

### 11.4 Decisions Versus Indicators
A large number of decisions can be supported by error budget-based decision-making using the SRE indicators from the previous chapters. 

> See table 11.5 to illustrate Decisions Supported by the SRE Indicators

### 11.5 Decision-Making Workflows
SRE indicators will be used to demonstrate how error budget–based decision–making can be practiced to support the most important and frequent reliability decisions, such as the following:

- Decision to consume an API
- Decision to tighten a dependent service's SLO
- Decision to invest in new features versus reliability
- Decision to set an SLO
- Decision to set an SLA 
- Decisions to allocate SRE capacity to a team
- Decisions to select a hypothesis for chaos engineering

#### 11.5.1 API Consumption Decision Workflow
A decision to consume an API can be supported by a three-step workflow. The workflow is rooted in three questions.

- Which SLOs are defined for a service
- What is the adherence to the SLOs? 
- What is the SLO error budget depletion trend? 

- Three-Step Workflow Supporting an API Consumption Decision

| Step | SRE Indicator | Explanation | 
|----|----|----|
| 1 | "SLOs by Service" indicator | Shows the SLOs defined for a service whose APIs are considered to be consumed |
| 2 | SLO adherence indicator | Shows the adherence to the defined SLOs over time | 
| 3 | SLO errer budget depletion | Shows the error budget depletion trend that can be used for exploration purposes |

When considering consuming an API exposed by a service, the first thing to find out is whether there are any SLOs defined for the API. This can conveniently be done using the “SLOs by service” indicator. The table settings enable the user to easily find the right service, select the target deployment of interest, and explore the SLOs by SLI.

If there is no SLO defined for the API considered for consumption, the workflow cannot be executed. The team considering API consumption needs to get in touch with the team owning the service and ask them to set SLOs for the API. This is a great opportunity to define the SLOs together, discussing the customer use cases intended to be fulfilled.

If there are SLOs defined for the relevant API, they can be analyzed for their suitability to fulfill the intended customer use cases. In the next step, SLO adherence by the service over time can be viewed by clicking on the link in the SLO adherence column of the “SLOs by service” indicator table.

Using the three-step workflow and looping through the steps as required, the user can learn a great deal about the historical reliability of the API considered for consumption. The following questions become clarified.

- What are the SLOs defined for the API? 
- What is the historical adherence to the defined SLOs in the intended target environments? 
- What was the error budget depletion trend in the error budget periods where the SLO was fulfilled? 
- What was the error budget depletion trend in the error budget periods where the SLO was broken? 
- How does the error budget depletion trend correlate with the service deployments? 
- How quickly is the error budget depletion stopped on average? 

This wealth of reliability knowledge about the service considered for consumption enables a very conscious decision-making process. 

#### 11.5.2 Tightening a Dependency's SLO Decision Workflow 
After a team has looked at an SLO definition of another team’s APIs that they are considering consuming, adherence to the SLO in the target environment, and SLO error budget depletion, they might conclude that the SLO needs to be tightened. 

> From the Trenches: The new conversations between the teams do not happen just because of the availability of SRE indicators. To get the new conversations going, they need to be facilitated by the SRE coaches. Initially, this means going team by team as part of the regular SRE coaching meetings.
In the meetings, the SRE coaches need to inquire about the plans to consume APIs owned by other teams. Based on the plans, the coaches need to facilitate the decisions to consume the APIs using the SRE indicators. They need to demon- strate the new decision-making workflows, such as the API consumption decision workflow (Section 11.5.1) and tightening a dependency’s SLO decision workflow (Section 11.5.2).
This will need to be repeated a couple of times by each team. Depending on the ease of use of the SRE indicators and the effectiveness of the conversations between the teams, the new way of considering API consumption will start mak- ing its way into ongoing practice.

#### 11.5.3 Features Versus Reliability Prioritization Workflow 
Decisions regarding investing in new features versus reliability for a given period of time in the future are at the heart of SRE. These decisions constitute the core prioritization workflow exercised regularly by the product owners. The SRE indicators provide a great deal of support in making these decisions in a data-driven manner.

A decision to invest in features versus reliability can be supported by a five-step workflow. The workflow is rooted in the following five questions:

1. Which service endpoints break the error budget in most error budget periods? 
2. Which service endpoints have the least time to error budget exhaustion and the least error budget available? 
3. Which service endpoints have the highest error budget depletion speed? 
4. Which service endpoints are the least available? 
5. Which service endpoints are the slowest? 

- Five-Step Workflow Supporting a Decision to Invest in Features Versus Reliability 

| Step | SRE Indicator | Explanation |
|----|----|----|
| 1 | SLO Adherence indicator | Shows the adherence to the defined SLOs over time by error budget |
| 2 | Premature SLO error budget exhaustion indicator | Shows service endpoints that exhaust the SLO error budgets prematurely, as well as the time to error budget exhaustion and the error budget shortage at the end of each error budget period |
| 3 | SLO error budget depletion indicator | Shows the error budget depletion speed by service endpoint |

Each indicator returns a set of service endpoints. In order to limit the returned results, it is advisable to take a certain number of services (e.g., three) from the top of each indicator’s result list. This will yield a manageable number of the most critical service endpoints to be taken for reliability improvements.

- Characteristics of Service Endpoints in Most Need of Reliability Improvements

| Workflow Step | Indicator | Depends on SLO | View Across Error Budget Periods | Characteristics |
|----|----|----|----|----|
| 1 | SLO Adherence indicator | Yes | Yes | Long-term error budget breakers |
| 2 | Premature SLO error budget exhaustion indicator | Yes | No | Short-term fastest error budget exhausters, short-term biggest error budget shortage by error budget period | 
| 3 | SLO error budget depletion indicator | Yes | No | Short-term fastest error budget depletors |
| 4 | Least available service endpoints indicator | No | No | Short-term least available endpoints |
| 5 | Slowest service endpoints indicator | No | No | Short-term slowest endpoints |

#### 11.5.4 Setting an SLO Decision Workflow
An SLO needs to have a number of characteristics to be good. Most importantly, a good SLO needs to reflect well on the user experience of a specific step in a specific user journey and, when broken, lead to a fast and clear understanding of how the user experience is impacted. That is, setting an SLO needs to be rooted in user experience.

Another dimension to think about is that the dependent services might become unavailable either at the same time or at different times. These temporal effects may impact the service level that can be offered to users. 

Digging deeper, some dependent services might have SLOs or SLAs published. Others might not. Furthermore, some dependent services might have the historical adherence to the SLOs or SLAs published. Others might not.

This discussion shows that setting an SLO is not a fully straightforward process. The aim is to set the SLO in such a way that it reflects the user experience well. This can be done empirically by setting an initial SLO to a seemingly appropriate value and iterating quickly based on SLO breaches. While iterating on SLO breaches is an inherent part of achieving a good SLO, setting an initial SLO can be supported well by data.

In a service network, the SLOs and SLAs of dependent services owned by the product deliv- ery organization should be public information, as should the historical adherence to the SLOs and SLAs. This data can be used to estimate the impact of the dependent services’ reliability on the service whose SLOs are being set.

As to the dependent services not owned by the product delivery organization, some of them may have SLAs exposed. Historical adherence to the SLAs might be exposed as well. That is, the process of setting an SLO for a service can be supported by analyzing the available data on and the historical adherence to the SLOs and SLAs of internal and external dependent services.

If a service has SLOs and SLAs defined, it is worth looking at both of them and their adherence. SLOs are typically set at a higher service level than SLAs. This is done in order for the SLOs to be higher internal targets than contractually agreed SLAs. 

A decision to set an SLO for a service can be supported by a four-step workflow to be exe- cuted for each dependent service. The workflow is rooted in the following four questions.

1. Does the dependent service have SLAs? What are they? 
2. Are the SLAs fulfilled over time? 
3. Does the dependent service have SLOs? What are they? 
4. Are the SLOs fulfilled over time? 

Answering the questions is directly supported by four SRE indicators:

- Four-Step Workflow Supporting a Decision to Set an SLO

| Step | SRE Inidcator | Explanation |
|----|----|----|
| 1 | "SLAs by service" indicator | Shows the SLAs defined for a service, if any |
| 2 | SLA adherence indicator | Shows the adherence to the defined SLAs over time by error budget period |
| 3 | "SLOs by service" indicator | Shows the SLOs defined for a service, if any |
| 4 | SLO adherence indicator | Shows the adherence to the defined SLOs over time by error budget period |

Using the indicators, it may be possible to find out the highest service level offered by a dependent service. The service levels could be categorized as follows:

- Undefined: if neither SLOs nor SLAs are set for the service
- Low: if SLAs and SLOs are defined but broken 
- Medium: if SLAs are defined and fulfilled 
- High: if SLOs are defined and fulfilled 

#### 11.5.5 Setting an SLA Decision Workflow
Setting an SLA involved two parts: technical and contractua. Technically, if a service has a well-defined SLO already, it can and should be used as a basis for the technical SLA definition. In this case, the SLA will be a relaxed version of the SLO. 

The contractual part of setting an SLA will involve negotiations with customers and part- ners. The negotiations can be supported by data provided by the SRE indicators. What is important in the negotiations is knowledge of the risk that can be accepted by the product delivery organization. Specifically, it is about the risk of the following:

- Tightening an SLA in the contract 
- Contractual penalties of breaking the SLA

The workflow consists of three steps. It is rooted in the following three questions: 

1. What is the incident time to recovery trend? 
2. If the incident recovery time trend is declining, what is the SLA adherence trend? 
3. If the historical SLA adherence is acceptable, what is the typically remianing SLA error budget by error budget-period? 

- Three-Step Workflow Supporting a Contractual Decision to Tighten an SLA

| Step | SRE Indicator | Explanation |
|----|----|----|
| 1 | Incident time to recovery trend | Shows the historical incident recovery time trend |
| 2 | SLA adherence indicator | Shows the historical SLA adherence |
| 3 | SLA error budget depletion indicator | Shows the historical SLA error budget depletion |

In workflow step 1, the incident time to recovery trend is determined for the teams and services involved in the SLA negotiations. The incident time to recovery trend is an indicator of whether a team might be overburdened if their SLAs were to be tightened. The trend shows the recovery time from the incidents based on the current SLAs. If the SLAs were to be tightened, more incidents need to be assumed, to be on the safe side for negotiation purposes. If the current incident time to recovery is trending upward, the assumption for negotiation purposes needs to be that more incidents in the teams would lead to even longer times to recovery. 

If, however, the current incident time to recovery trend is steadily declining, it might be an indication that more incidents, assumed to happen due to the tightened SLAs, could be handled by the team. In order to explore this question, in workflow step 2, the SLA adherence trend can be seen. If the historical adherence to the SLAs is appropriate in that the SLAs were successfully defended in most of the error budget periods of the selected time window, it might be another indication that the team might be able to defend the tightened SLAs.

In order to test this hypothesis, in workflow step 3, the remaining SLA error budget at the end of the error budget periods can be looked at. If the error budget remaining at the end of the selected error budget periods is significant (e.g., over 25%), there is a reason to believe that tightening the SLAs will not overburden the team. Indeed, three indicators hint at that.

1. The team's incident time to recovery is trending downward.
2. The adherence to the current SLAs is sufficient. 
3. The remaining SLA error budget by error budget period is significant. 

#### 11.5.6 Allocating SRE Capacity to a Team Decision Workflow
Personnel decisions regarding SRE capacity allocation to a team are subject to a number of con- straints. Budget availability constraints, budget distribution difficulties, situations that are difficult to untangle due to ambiguous statements by different people claiming the budget and head count, high-stakes conversations including blame, and other constraints might stand in the way of transparent decision-making. SRE indicators provide good assistance in making SRE capac- ity allocation decisions in a data-driven manner.

A decision to allocate SRE capacity to a team can be supported by a four-step workflow. The workflow is rooted in the following four questions.

1. What is the SLO adherence by error budget period by the services owned by the team? 
2. How many people are involved in the on-call rotation, if any? 
3. What is the customer support ticket trend for the services owned by the team? 
4. What is the incident time to recovery trend in the team? 


- Four-Step Workflow to Support a Decision to Allocate SRE Capacity

| Step | SRE Indicator | Explanation |
|----|----|----|
| 1 | SLO adherence indicator | Shows the adherence to the defined SLOs over time by error budget period |
| 2 | "On-call rotations" by team indicator | Shows the number of people involved in on-call rotations by team |
| 3 | Customer support ticket trend | Shows the customer support ticket growth trend for services owned by a team |
| 4 | Incident time to recovery trend | Shows the incident time to recovery trend for a team |

Signs that a team needs more SRE capacity allocated in order to adequately support the services they own in production are:

- The SLO adherence by error budget period is low.
- The on-call rotations by the team are not adequately manned. 
- The customer support ticket trend for the services owned by a team is growing. 
- The incident time to recovery trend is growing


Using the data from the four SRE indicators, the signs can be read and used in decision-making conversations. To be sure, the SRE indicators data can only assist in these conversations. The data alone should not determine personnel and budget allocation decisions directly! Once the decisions are made, SRE capacity allocation can be executed in different ways depending on the SRE setup in the product delivery organization.

If developers perform the SRE work in the teams, a decision to add a developer to the team might be made. Alternatively, a decision to reallocate the ownership of services might be made in order to provide each team with enough capacity for doing the SRE work. If the operations engineers also perform the SRE work for product services, a decision might be made to allocate an operations engineer to a team.

#### 11.5.7 Chaos Engineering Hypothesis Selection Workflow
Chaos engineering is a software discipline formed at the end of the 2010s with the purpose of increasing system resilience. It is defined by Principles of Chaos Engineering as “the discipline of experimenting on a system in order to build confidence in the system’s capability to with- stand turbulent conditions in production.” “Hope is not a strategy” is a traditional SRE saying that aligns well with chaos engineering’s philosophy of experimentation.

- Chaos Enginering Experiment Structure 

| Step | Description | Explanation |
|----|----|----|
| 1 | Define a steady state of the system | This can be defined using relevant business metrics measured in real time showing that hte system is healthily working as expected from teh user point of view |
| 2 | For a hypothesis | A hypothesis about the steady state remaining grossly unchanged when some harm is inflicted to the system.
The hypothesis can be specified using, for example, the "capability" / "outcome" / "measurable signal" triple (see Section 4.7, Posing Hypotheses). The capability in this case is the planned harm to the system. The expected outcome is the maintenance of the steady state. The measurable signal specifies how the steady state will be measured during the experiment. |
| 3 | Simulate real-world events | This is the phase of inflicting the harm to the system planned in the hypothesess. It can include all kinds of adversary technical actions. For instance, shutting down a data center region, multiplying the network latency in a network, and random shutdown of services are typical examples of how real-world events are simulated. |
| 4 || Test the hypothesis | In this phase, the actual system state during the harm infliction is compared to the steady state defined in the first step. If the steady state is maintained despite the harm, the hypothesisis proved. The learning is that the system is as reliable as hypothesized before. If the steady state is not maintained, the hypothesis is disproved. The learning is in the new system weaknesses that got uncovered. These need to be prioritized to improve the system reliability. |

That is, a steady state of the system can be defined using SLOs. A hypothesis to test can also be defined using the SLOs. Testing the hypothesis can be done using SRE indicators. In addition, the search for hypotheses to test using chaos engineering experiments can be supported by the SRE indicators as well.

A decision to select a hypothesis can be supported by a three-step workflow. The workflow is rooted in the following three questions.

1. Which SLOs are defined for which services?
2. What is the adherence to the SLOs on different time scales? 
3. Are there any unusual error budget depletion patterns for successfully defended SLOs? 

The goal is to find services that consistently defend their SLOs successfully and try to break them using chaos experiments; and, on an exploratory basis, to investigate the error budget depletion patterns aiming to find cases where the error budget defense is strong but the reasons for that are either unknown or opaque.

- Three-Step Workflow to Support a Chaos Engineering Hypothesis Selection Decision

| Step | SRE Inidcator | Explanation |
|----|----|----|
| 1 | "SLOs by serice" indicator | Shows the SLOs defined for a service, if any |
| 2 | SLO adherence indicator | Shows the adherence to the defined SLOs over time by error budget period |
| 3 | SLO error budget depletion indicator | SHows the error budget depletion trend that can be used for exploration purposes | 

At the end of a chaos experiment, if a hypothesis is proven wrong, the steady state of the system is significantly changed. This provides the teams owning the respective services with valuable data to improve service reliability. Additionally, the data might give rise to the creation of new or the adaptation of existing SLOs.

- Structuring Choas Engineering Experiments 

| | Known | Unknown | 
|----|----|----|
| Known | Testing for "Known Knowns" <ul><li>Awareness: exists</li><li>Understanding: exists</li></ul> | Experimenting for "Known Unknowns" <ul><li>Awareness: exists</li><li>Understanding: does not exist</li></ul> |
| Unknown | Checking "Unknown Knowns" <ul><li>Awareness: does not exist</li><li>Understanding: exists</li></ul> | Looking at "Unknown Unknowns" <ul><li>Awareness: does not exist</li><li>Understanding: does not exist</li></ul> |

An example of a “Known Known” is a cloud service auto-restart on service shutdown with the auto-restart setting switched on. When switching on the setting, there is an understanding that a service restart can happen. The reason to switch on the auto-restart setting provides awareness of the situations where the restart is necessary.

An example of a “Known Unknown” can be the time frame for a cloud service auto-restart on service shutdown with the auto-restart setting switched on. The time frame might be significant for the reliability of important use cases. There is awareness that the service auto-restart will happen. However, there is no understanding of how long it would take due to, for example, the cloud provider not publishing an SLA for the auto-restart duration.

An example of an “Unknown Known” is when a cloud service is deployed in a shared service plan with many other services sharing resources such as memory, storage, and so on. The cloud provider may have a recommendation for the maximum number of services in the plan to optimize resource consumption and avoid resource starvation by the deployed services. However, there might be no native way to enforce the recommended limit. In this case, after a service auto-restart, it is unknown whether the service will get enough resources allocated by the service plan. In fact, resource starvation might be the reason for the service auto-restart in the first place. The understanding of the situation is there but it is beyond perception what would actually happen in terms of resource allocation after the service auto-restart.

An example of an “Unknown Unknown” is when there is no experience with a cloud service auto-restart in case of a simultaneous failure in the cloud provider’s compute service. The failure could be small scale or encompass an entire data center region. According to the cloud provider’s SLAs, this can happen. However, it was not experienced in the past. There is no understanding and very little awareness of what would happen in this case.

In “Chaos Engineering: the history, principles, and practice,”9 the Failure as a Service company Gremlin argues that chaos experiments should be performed in the following order:

1. Known Knowns
2. Known Unknowns 
3. Unknown Knowns
4. Unknown Unknowns 

--
EoF