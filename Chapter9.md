# Chapter 9 - Implementing Incident Response
By now the teams have defined SLOs in an iterative manner, implemented on-call rotations to react to SLO breaches, and set up stakeholder notifications to keep stakeholders abreast of major outages. With that, the basics of an incident response process are laid down in the product delivery organization: Inci- dents are being detected and worked on by the teams, and the stakeholders are being informed about major outages before customers complain. 

The next evolutionary step in the incident reponse process is to define an incident classification scheme and set up appropriate responses based on incident class. 

### 9.1 Incident Repsonse Foundations
An incident is defined as: An event that could lead to loss of, or disruption to, an organization's operations, services, or functions.

ITIL specifies a detailed incident response process that has five steps. 
1. Incident identification
2. Incident logging
3. Incident categorization
4. Incident prioritization
5. Incident response 
    - Initial diagnosis
    - Incident escalation
    - Investigation and diagnosis
    - Resolution and recovery
    - Incident closure 

With the SRE methodology in place, the preceding steps are covered to some degree. The goal of defining an incident response process is to strengthen the points where necessary to achieve a robust and repeatable process for handling incidents. The process needs to be defendable in audits of various kinds. This generally means it needs to be written down and adhered to. Further, the evidence of process adherence needs to be produced on request.

### 9.2 Incident Priorities
So far, the SLOs and, consequently, the SLO breaches were not assigned explicit priorities. This does not mean the teams did not prioritize them internally. They probably did, in order to know which SLO breaches are more important than others and to act accordingly. To strengthen the incident response process, more consistent, explicit, and transparent SLO prioritization needs to take place.

- SRE coaches need to initiate a generic definition of incident priorities for the product delivery organization. 
- Teams will use the generically defined incident priorities to categorize their SLOs accordingly within the unique contexst of their domain. 
- This will result in cross-domain standardization of incident priorities used by all the teams in the organization. 
- Alignement on incident priority, this standardization allows for everyone to be able to speak to the priority in the same manner, regardless of the domain they support. 

> See figure 9.1 Organization-wide incident priorities versus team-local SLOs

> See figure 9.2 Mapping team-local SLOs to the organization-wide incident priorities

In terms of tool support, setting incident priorities is supported by all common on-call management tools available on the market. 

#### 9.2.1 SLO Breaches Versus Incidents 
The organization-wide incident priorities need tob e defined in a distinct way without overlap between them.
- Incident classification should be unique and have no overlap. Overlap adds ambiguity. 
This is also neccessary to ensure unique assignments of SLOs to the incident priorities. Based on the unique incident priorities assigned to an SLO, all incidents based on the breaches of that SLO should be assigned the incident priority. The people on call can do this either autmatically or manually. 

> See figure 9.3 Incident priority versus SLO breaches. 

An SLO has exactly one incident priority assignment. An SLO can have many SLO breaches. All SLO breaches of an SLOW get the SLOs incident priority assigned when the breach occurred. 
As the incident unfolds, the people on call may change its priority based on the situational context and thier judgement of the matter. The incident priority may get lowered or elevated as a result. 

> See table 9.1 SLO Breaches versus Incidents

- The SRE coahces need to stage the implementation of that feature in the SRE infrastructure by the operations teams to be done in time for the incident priorities being defined by the teams owning the services. 

#### 9.2.2 Changing Incident Priority During an Incident
During an incident investigatino, the people on call may change the incident priority based on ongoing learnings, refined context, and new details 

> The above varies from standardized incident response where incident priority is not discussed during an active incident bridge.

> Figure 9.5 Example of incident priority changes while the incident unfolds 

#### 9.2.3 Defining Generic Incident Priorities
Incident priorities need to be defined so that it is easy for a person on call to dynamically decide on an incident priority as the incident unfolds. 

- Therefore, the set of criteria for an incident priority should be very short

To drive the definition of generic incident priorities, the SRE coaches need to start with the operations teams. There may already be some existing definitions for incident priority when you start this step. 

The SRE coaches with the operations teasms need to propose a small set of incident priorities with a proportionally small set of criteria describing each priority. The incident priorities should provide direction on the following dimensions: 

- Which actions must be taken? 
- Who has to be informed about the issue and the actions being taken? 

> See Table 9.2 Sample Incident Priorities

Incident priority 1 describes situations that require an immediate hotfix rollout and a later
postmortem. The product delivery organization’s management team and the stakeholders need
to be notified about the outage. The teams themselves select the stakeholder groups when assigning priorities to the SLOs. Incidents with a priority of 1 represent outages with severe customer impact. Therefore, these incident status updates need to be broadcast to the stakeholders every two hours.

A generic example of an incident with priority 1 would be when no log-on to any application
is possible (think: Amazon or Twitter log-on does not work). Concrete examples of priority 1
incidents will be defined team by team in their respective domains when they go through their
SLOs to find the ones that, when broken, would correspond to the five criteria in Table 9.2

Next, incident priority 2 describes situations that do not require a hotfix to be rolled out. Likewise, no postmortem is required. However, these situations deserve some attention from management and stakeholders. Therefore, notifications to them are required and need to be sent out every four hours. 

A generic example of a priority 2 incident is when an application experiences a more than
70% drop in average daily user log-ons in a data center. In this situation, the reasons for the drop in log-ons may be manifold. It might be because a festival being held in the region is taking people away from their work, and therefore they are not using the application because the application only applies to situations in business settings. It might be because internet connectivity in the region was impacted due to a natural disaster. Or it might be because of a network slowdown in the region with the cloud provider of choice, which can be rectified only by the cloud provider itself. In situations like these, the stakeholders and the management team need to be aware of the outage and receive a progress update every four hours. More, however, cannot be done by the product delivery organization if the reasons for the drop in number of log-ons are beyond their control. 

Finally, incident priority 3 describes situations where no hotfix, postmortem, or management notification is required. However, the issue at hand is affecting the work of customers or stakeholders to the point where specifc stakeholder notifications need to be broadcast to make them aware of the issue ahead of time. The issue is not that pressing. Therefore, status updates every eight hours should be sufficient. 

The SRE coaches should ensure that the initial propoasal of generic incident priorities does not contain more than five priorities. Each priority should not be defined using more than five criteria. Simplicity and unambiguity are more important than precision and detailedness here. 

- Have defines SLOs in an iterative manner
- Have an on-call rotation in place
- Use the on-call management tool
- Are looking to streamline their incident response process by prioritizing SLO breaches 

> Key Insight: The final definition of the generic incident priorities, and how to use them, needs to be put onto the SRE wiki. This way teams can easily reference the definition while prioritizing their SLOs. 

#### 9.2.4 Mapping SLOs to Incident Priorities
With the generic incident priorities defined, the SRE coaches should bring the topic of prioritizating the SLO breaches to the development teams that are ready, in order to streamline the incident response process. 

- This can be done through a regular cadence for SRE coaching sessions. 

For example see Table 9.3 Sample SLO Use Cases in a Team 

| # | SLO Use Case | SLI 
|----|----|----| 
| 1 | Application cannot register with notification services | Availability |
| 2 | Application cannot notify its users | Availability |
| 3 | Notifications arrive with a delay | Latency |
| 4 | Notification preferences cannot be set | Availability |
| 5 | Notifications are sent in the wrong langauge | Correctness |

For each SLO, the team needs to decide what incident priority they think is appropriate when the respective SLO gets broken. For instance, the team might make these decisions using the sample incidnet priorities from the previous section (Table 9.4) 

| # | SLO | Incident Priority |
|----|----|----| 
| 1 | Application cannot register with notifications services | 2 |
| 2 | Application cannot notify its users | 2 |
| 3 | Notifications arrive with delay | 3 |
| 4 | Notification preferences cannot be set | None |
| 5 | Notifications are sent in the wrong language | None |

In the above example the team decided to not use incident priority 1 for any SLOs because the services sending notifications to users are not critical in the product's domain. 

The exercise of setting the incident priorities undertaken by the team might give rise to additional requests to the SRE infrastructure. For example, a team might conclude that a use case, when broken once, would warrant a priority 4 incident. However, when broken more than three times within an hour, it would warrant a priority 2 incident. Requests like this should be carefully collected and put onto the SRE infrastructure backlog for the operations teams to prioritize and work on. Additionally, the need to support new SLIs or new wasy to measure existing SLIs can be uncovered while deciding on incident priorities for SLOs. 

The SLOs’ incident priorities set by the teams need to be set in the SRE infrastructure. The
priorities need to be made public for reference by everyone in the product delivery organization. The reference to the SLO priorities in the SRE infrastructure also needs to be added to the runbooks so that they are readily available for the people on call. 

#### 9.2.5 Mapping Error Budgets to Incident Priorities
It may be possible to generically map domain use cases in the teams to incident priorities as a function of error budget depletion for a given SLO breach. 

Mapping Error Budget Depletion Thresholds to Incident Priorities

| Incident Priority | Use Case Expressed as Error Budget Depletion Threshold on SLO Breach |
|----|----|
| Priority 1 | 20% of the error budget is left within a given time unit, and with the current error budget depetion trend, the error budget will be exhausted prematurely |
| Priority 2 | 40% of the error budget is left within a give time unit, and with the current error budget depletion trend, the error budget will be exhausted prematurely |
| Priority 3 | 60% of the error budget is left within a given time unit, and with the current error budget depletion trend, the error budget will be exhausted prematurely |
| Priority 4 | 80% of the error budget is left within a given time unit, and with the current error budget depletion trend, the error budget will be exhausted prematurely |

Mapping Error Budget Depletion Velocity to Incident Priorities
| Incident Priority | Use Case Expressed as Error Budget Depletion Velocity on SLO Breach |
|----|----|
| Priority 1 | More than 75% of the monthly error budget was depleted within five consecutive minutes |
| Priority 2 | More than 50% of the montly error budget was depleted within 10 consecutive minutes |
| Priority 3 | More than 25% of the monthly error budget was depleted within 15 consecutive minutes |
| Priority 4 | More than 25% of the monthly error budget was depleted within 20 consecutive minutes |

While the above is technically feasible, this seems to be too mechanical to be applied generally and reflect reality weill. However, this kind of logic might be an idea to explore to set incident priorities for the SLO breaches whose SLOs do not have an explicit incidnet priority assigned. 

#### 9.2.6 Mapping Resource-Based Alerts to Incident Priorities 
When the SRE coaches guide a team through their SLOs to define incident priorities for them,
only the use cases covered by the SLOs are considered. To broaden the scope of coverage by the
incident priorities, the SRE coaches should also encourage the teams to go through the resource based alerts they might have and assign incident priorities to them, as well. The assignment works much the same way as with the SLOs

- As the SRE infrastructure matures and starts supporting the use cases currently covered by the resource-based alerts, these alerts should be replaces with proper SLOs. Doing so enables a whole host of improvements out of the box. 

SLI vs Just Alerts 

SLI 
- Visualizations for error budget-based-decision-making
- Visualizations for error budget consumption
- Alerting algorithm
    - Timelines
    - Effectiveness
- SLO Breaches

Just Alerts 
- Resource-Based alerts 

Big differences seen almost immediately. 

With the switch from resource-based alerts to alerts on SLO breaches, the alerting algorithm
implemented in the SRE infrastructure is used to send out the alerts. It does not alert immediately on every SLO breach, but rather implements features of timeliness, effectiveness, and others to strike a good balance in order to reduce alert fatigue. Moreover, visualizations of error budget depletions are enabled. Likewise, additional visualizations for error budget–based decision–making are unlocked.

- Make sure the development teams know what options they have within the SRE infrastructure that can be used to switch from resource-based alerts to the SLI/SLO models. 

- The SRE coaches needd to make sure the teams understand the difference between resource-based alerts and SLI/SLO. It needs to be clear. 

#### 9.2.7 Uncovering New Use Cases for Incident Priorities
In addition to mapping the existing SLOs and resource-based alerts to teh generic incident priorities, the definition of the priorities can be used as a source of inspiration to define new alert use cases that have not yet been covered. 

The SRE coaches should encourage the teams to use the incident priority definitions to uncover new use cases. 

1. Take the definition of generic incident priorities
2. For each incident priority, think about new use cases in the team's domain not covered by existing monitoring that would warrant actions stipulated by the priority.
3. For each use cases discovered in this way, think about how it could be monitored:
    - Could it be monitored by a new SLO of an existing SLI?
    - Could it be monitored by a new SLO of a new SLI?
    - Could it be monitored by a new resource-based alert? 
An analysis like this is going to uncover the need for new SLIs or new ways to meaure existing SLIs to be supported by the SRE infrastructure. These requests should go direclty to the SRE infrastructure backlog for the operations teams. To cover the use cases that are relavant but not yet supported by the current SRE infrastructure, resource-based alerts should be defined and handled as described in the previous sections. 

#### 9.2.8 Adjusting Incident Priorities Based on Stakeholder Feedback
The next step is to get stakeholder feeeback on the priorities and adjust them as neccessary. The SRE coaches need to organize these feedback sessions. The sessions are neccessary to reconcile the views of service providers and service consumers regarding the incidnet priority of a given outage. 

Service provider teams defined the incident priorities based on their understanding of the importance of a given functionality to an average consumer of the service. Because of the plurality of service consumers, each potentially operating in a serpate subdomain, different consumers will have different views on the incident priority for an outage of a given functionality. 

- Sample Views on the Incident Priority of an SLO Breach

| SLO Breach Use Case | Service Provider's View on the Incident Priority | Service Consumer 1's View on the Incident Priority | Service Consumer 2's View on the Incident Priority |
|----|----|----|----|
|Application cannot notify users | 2 | 1 | 3|

In a bigger service network of a microservices architecture or public API used by many third parties, it will not be possible to ask all the stakeholders. It follows that the feedback on the incident priorities will be orientational at most. Still, iterating on the orientational feedback is better than soliciting no feedback at all. 

The final decision about the incident priorty after considering the feedback from teh stakeholders remains with the service provider team. It is their service and service incidents, after all. 

- Strategy Dimensions for Coping with Dependent Service Outages

| Strategy Dimension | Explanation | 
|----|----|
| Adaptive capacity | The amount of adaptive capacity between a service consumer and a service provider can be increased if the incident priority from the consumer point of view should be higher than that set by the service provider. This is because the service provider will fix the respective outages with lower priority than the priority wished for by the service consumer. This is going to lead to a longer time to recover from the outages. During that time, the users of the service consumer need to be kept operational with degraded functionality |
| Stakeholder notifications | If the incident priority from the consumer point of view should be higher than that set by the service provider, the service consumer might wish to implement a stakeholder group to notify their people on call when there is an outage in the service provider. The people on call in the service consumer team will evaluate the outage notification and, if degraded functionality cannot be provided, might decide to notify their own stakeholders about the outage, rephrasing it for thier domain. |

#### 9.2.9 Extending the SLO Definition Process
In the teams that defined incident priorities for their existing SLOs once, the SLO definition process can be extended in the future. After a new SLO is set, its associated incident priority can be set by the team using the generic incident priority definitions. 

- It needs to be noted, that this is only beneficial for the teams that are further ahead on the SRE transformation journey. 
- Teams that are only fefining initial SLOs are not yet read for incident priority definition. Trying to define incident priorities in addition to the initial SLOs themselves is a distraction at the moment.

#### 9.2.10 Infrastructure
Which SLO breach-based alerts and resource-based alerts being the origins for incidents, the entire infrastructure setup is growing a bit more complex. 

#### 9.2.11 Deduplication
Incidents originate from SLO breaches and resource-based alerts. Both have a characteristic that they may occur many times for the same root causes as teh incident unfolds. 

- Example Settings for a Resource-Based Alert on CPU Consumption

| Setting | Operator | Value |
|----|----|----|
| Host | = | ABC |
| CPU | > | 90% |
| Aggregation | Average | 15 Minutes |
| Evaluation Frequency | = | 15 Minutes |
| Alert | = | 5 Minutes |
| Name | = | "CPU>90% on host ABC" |

- Example Settings for an Availability SLO Breach 

| Setting | Operator | Value |
|----|----|----|
| Endpoint | = | @GET/api/data/{tenant} |
| SLI | = | Availability | 
| SLO | = | 99.7% |
| Error Budget depletion for alert | > | 200% |
| Error Budget depletion window | = | 60 Minutes |
| Evaluation Frequency | = | 5 Minutes |
| Alert Snooze | = | 120 Minutes |
| Name | = | "Availability of get data API" |

This SLO breach=based alert is for availability of endopoint "@GET/api/data/{tenant}" 

### 9.3 Complex Incident Coordination 
So far, the incident priorities were defined. They help the people on call prioritize their work when several incidents pile up. Moreover, they help standardize actions taken for all incidents of a given priority across the product delivery organization. The incident priorities, however, typically do not say a lot about the complexity of an incident in terms of, for example, the number of teams required to resolve it. This dimension is explored in this section. 

#### 9.3.1 What Is a Complex Incident
Whenever an incident cannot be solved in a team where it originated and has to be distributed to other teams for further processing, it can be referred to as complex. That is, a complex incident involves more than one team to be resolved. According to PagerDuty, additional criteria may apply to complex incidents, such as the availability of multiple uncorrelated symptoms, several experts working on the same analysis, and so on. In the majority of cases, complex incidents will be assigned incident priority 1.

#### 9.3.2 Existing Incident Coordination Systems
In order to drive complex incident coordination, in the past entire systems were developed by
governments and professional groups such as firefighters, natural disaster rescuers, and medical emergency units. Notably, in the United States, an Incident Command System was developed. According to Wikipedia, “The Incident Command System (ICS) is a standardized approach to the command, control, and coordination of emergency response providing a common hierarchy within which responders from multiple agencies can be effective.” That is, the standardization of command, control, and coordination is at the heart of ICS. In the context of complex software incidents, coordination is especially important to enable efficient team swarming on the problem at hand.

In terms of software operations, Pager Duty defined a similar system with specific roles to coordinate complex incident response. 

- PagerDuty Incident Reponse Roles 

| PagerDuty Role | Purpose |
|----|----|
| Incident Commander | Overall driver of the incident toward resolution |
| Deputy incident commander | Supports the incident commander with detail coordination |
| Scribe | Ensures the incident is documented on an ongoing basis | 
| Internal Liason | Ensures internal stakeholders are informed appropriately |
| Customer Liason | Ensures customers are informed appropriately | 
| Subject matter expert | Domain expert responsible for a part of the system | 

The SRE coaches need to initate an engagement with the operations teams to study existing incident response systems such as ICS, that from PagerDuty, and any others. Together, they need to assess the complexity of the product delivery organization at hand and work to propose an appropriate process including roles to drive the coordination of coplex incidents. The proposed process needs to cover the following fundamental questions. 

1. When is incident coordination required? 
2. Who initiates incident coordination? 
3. Who is making decisions? 
4. How are the decisions communicated? 
5. Who is in charge of receiving the communicated decisions? 
6. Who has to follow the decisions? 
7. What is the freedom versus responsibility for the teams involved? 
8. Who is responsible for communication? 
9. Who is responsible for documenation? 
10. Who is reponsible for running the incident postmortem? 

Before answering these questions, the SRE coaches should poll the people who have been going on call on how complex incidents have been handled so far. There was no explicitly defined incident response process. So, the complex incidents were resolved in an ad-hoc manner. Knowing how it was done invaluable input to define an incident response process that would have the potential to sustainably improve the status quo. The goal is to define a repeatable and reliable process for handling complex incidents in an efficient and effective manner. 

#### 9.3.3 Incident Classification
Depending on the definiation, the incident priority may dictate the actions to be taken as part of incident resolution, such as hotfix rollout and management notification. 

| # | Incident Dimension | Example Definition |
|----|----|----|
| 1 | Incident Priority | What needs to be done during the incident | 
| 2 | Incident Severity | How should it be done organizationally |


#### 9.3.4 Defining Generic Incident Severities 
Similar to generic incident priority definitinos, inident severities also need to be defined in a generic way. 

| # | Criteria | Incident Severity "Critical | Incident Severity "Error" | Incident Severity "Warning | 
|----|----|----|----|----|
| 1 | Users affected | Majority | About 50% | Minority | 
| 2 | Teams required | > 2 | 2 | 1 |
| 3 | Team coordinator required | Yes | Yes | No |
|   | Example | No log-on possible to any application | Sporadic user auto log out of applications | Demo data not available in the showcase deployment |

The incident severithy needs to be set by the people on call in order to invoke a certain incident response process. In the preceeding example, the "critical" incident severity means the majority of users are affected, more than two teams are required to work on the incident, and the teams have to be coordinated by a dedicated team coordinator. 

An example of an incident with a “critical” severity would be if no log-on is possible to any application. Setting the incident severity level to “critical” invokes the highest level of incident response. All roles to be defined in the incident response process will have to be involved in the resolution of the incident.

The "error" incident severity means that about 50% of users are affected. To resolve the incident two teams will be required, and the teams will need to be coordinated by a dedicated coordinator. 

#### 9.3.5 Social Dimension of Incident Classification
The definitions of incident priority and severity from the previous sections are rule based. The rule suggests that the people on call should assign incident priority and severity by and large irrespective of the wider circumstances or context. 

Example: The “warning” incident severity from the previous section states that it applies only to incidents that affect a minority of the users. Based on that, it is possible to imagine an incident that affects only one customer due to a failure in a service owned by a single team. So, the incident should be assigned a “warning” severity. However, the single customer affected by the incident could turn out to be a really important customer. Therefore, the people on call might want to be extra cautious and, as an exception, set the severity of the incident to “criti- cal,” causing a full-blown incident response to unfold.

- The definition of customer is important to establish during the building of the incident management lifecycle. 
- Customer classification is not part of the "incident response process" at all. 

To take the example further, it is possible to imagine that the important customer has a powerful advocate in the product delivery organization. For instance, a senior vice president of product can be in close touch with the customer and be called to immediately fix the issue. Following that, the senior VP may consult the on-call management tool, find the corresponding incident, and join the conference bridge where the incident response is unfolding. On the call, the senior VP may outrank everyone and demand that the most senior engineers join the call.

This breaks the entire incident response process that was carefully set up before. First, the senior VP takes over incident command, overriding the incident coordinator. Second, the senior VP commands people currently not on call to troubleshoot the incident. Third, the senior VP, unaware of the incident response process details, is likely to break the incident stakeholder communication rules.

- The SRE coaches need to think through situations like this in advance and systematically prepare the organization for a structured incidet response in an attempt to minimize the likelihood of such chaotic situations occuring. 

- That is, the social dimension of incident classification will influence the rule-based definitions of incident priority and severity. 

- This is a very important aspect to be aware of. 

- The impact of the social dimension will differ depending on the organizational culture. 

- The most impact will be felt in power-oriented cultures, with the impact in rule-oriented cultures possibly situated in the middle. 

- The SRE coaches need to take this into consideration during the SRE Transformation

> Personal Insight: Plan, prepare, and draw clear delineations to prevent scope creep due to social dimensions during the incident response process

- Finally, the incident classification needs to support the people on call to rapidly figure out what can be successfully ignored and what to focus on immediately.

#### 9.3.6 Incident Priority Versus Incident Severity
In cases where the incident priority (e.g., what needs to be done) and incident severity (e.g., how to do it organizationally) are defined as separate dimensions, their cross product also needs to be defined. The definition needs to make clear whether every permutation of incident priority and severity should be possible.

> Refer to table in Chapter 9, Table 9.14 Incident Priority Versus Incident Severity

#### 9.3.7 Defining Roles
With the incident severities defined, the highest severity level will require all roles defined in the incident response to be involved in incident resolution. Role definition is the subject of this selection. 

Roles that are needed to fulfill four areas: 
1. Coordination
2. Communication
3. Documentation
4. Execution

The SRE coaches need to work with the operations teams to propse a set of roles and associatd responsibilities.

- Example Incident Response Roles, Responsibilities, and Skills

| Role | Responsibilities | Skills | 
|----|----|----|
| Incident Coordinator | Decision-Making, Team Coordination, Team Well-being, Running Postmortems | Decision-Making, Emotional intelligence, People motivation, People coordination, Communication |
| Incident Communicator | Communication toward teams, Communication toward internal stakeholders, Communication toward external stakeholders, Incident Documentation, Postmortem documentation, Postmortem results communication | Communication, Technical writing, Liasing with stakeholders | 
| Technical expert | Technical Analysis, Solution proposal, Solution implementation, Postmortem participation | Technical expertise, Communication |

It might happen that additional people would be necessary for decision-making. For example, a project manager might be needed because of their knowledge of the impact of changing time- lines on other internal and external stakeholders. Additionally, an operations engineer might be needed because of their knowledge of an incident’s impact on first level support distributed around the world.

The SRE coaches and operations engineers need to take these points into account when proposing the roles to be involved in the incident response process. They also need to carefully consider these decisions in light of the existing organizational culture. 

When it comes to naming the roles, the most appropriate role names in the context of a given organization can be freely chosen. The role name “incident coordinator” is chosen in the preced- ing example to deliberately point out the need for coordination tasks within the context of a team of fully responsible people on call. In the industry, the role name “incident commander” is used more often than “incident coordinator.” Having the word “commander” in the role name might suggest to the people on call that they are fully commanded by the incident commander. It might suggest that the incident would be owned by the incident commander and the individual experts are “contracted” by the commander to carry out individual tasks of their incident.

- Pick names for the groups as needed that fit the organizational structure and make sense to the teams they work with. 

#### 9.3.8 Roles Required by Incident Severity
With the definition of the roles involved in the overall incident response process, role assignment by incident severity needs to take place. For exemplary purposes, such a role assignment by inci- dent severity is shown in the table below. 

| # | Role | Incident Severity "Critical" | Incident Severity "Error" | Incident Severity "Warning" |
|----|----|----|----|----|
| 1 | Dedicated incident coordinator | Yes | Yes | No |
| 2 | Dedicated incident communicator | Yes | No | No |
| 3 | Dedicated technical expert | Yes | Yes | Yes |

#### 9.3.9 Roles on Call
With the roles involved in the incident response process defined, an on-call rotation needs to be set up for each role.

- Example Roles on Call 

| | Rotation Period 1 | Rotation Period 2 | Rotation Period 3 | Rotation Period 4 |
|----|----|----|----|----|
| Incident Coordinator | Person A | Person A | Person B | Person B | 
| Incident Communicator | Person C | Person C | Person D | Person D |
| Team 1 Technical Expert | Person E | Person F | Person G | Person E |

#### 9.3.10 Incident Response Process Evaluation 
The incident response process proposed by the SRE coaches and operations teams consists of a complex incident definition, roles, responsibilities, incident priorities, and possibly, incident severities.

- Sample Incident Response Process Evaluation 

| # | Incident Response Process Criterion | Sample Fullfillment | 
|----|----|----|
| 1 | When is incident coordination required? | For incidents with severity set to "critical" or "error" |
| 2 | Who initiates the incident coordination | A person on call by setting the incident severity to "critical" |
| 3 | Who is make decisions? | The incident coordinator but not in a rigid command and control manner |
| 4 | How are the decisions communicated? | In a dedicated channel created for the incident automatically by the on-call management tool |
| 5 | Who is in charge of receiving the communicated decisions? | The people on call in the development and operations teams |
| 6 | Who has to follow the decisions? | The people on call in the development and operations teams |
| 7 | What is the freedom versus responsibility for the teams involved? | Freedom: Select technical solutions. Responsibility: Receive decisions from the incident coordinator, Execture on the decisions, Report on the execution status |
| 8 | Who is responsible for communication? | Incident severity "critical": incident coordinator Incident severity "error": incident communicator |
| 9 | Who is responsible for documentation? | The incident communicator |
| 10 | Who is responsible for running the incident postmortem | The incident coordinator |

The proposed incident response process needs to undergo a thorough review. The operations teams need to own the process and should initiate the review. To do so, the process needs to be documented in draft form on the SRE wiki. This way, the reviewers will be able to comment on the process easily. Furthermore, the changes proposed and made by anyone will be fully transparent. The list of reviewers needs to include everyone who has been going on call so far. These are the people who have been coordinating complex incidents in some ad-hoc manner. They are best equipped to assess how much the proposed incident response process would streamline the resolution of complex incidents.

#### 9.3.11 Incident Response Process Dynamics 
Using the incident response process should be easy. Keep your processes simple. For additional information see Figure 9.11 in Chapter 9. 

#### 9.3.12 Incident Response Team Well-Being
This responsibility deserves special consideration. It is rarely described in the literature but has a great impact on the success of an organization’s incident response.

When an incident unfolds, a team of the people on call is dynamically assembled. Over time, a complex incident might involve a dozen or more people. It is the incident coordinator’s responsibility to not only coordinate the people but also ensure their well-being as individuals and as a team.

Fullfilling this responsibility isn't always a straightforward task. For instance: 

- The incident coordinator may not personally know all the people on call who have been assigned to the incident. 
- These people may have never worked together as a team
- Some of them may be working beyond normal business hours after having spent an exhausting day at work. 

To top it all off, if the incident severity is “critical,” the entire team is, by definition, working in a high-pressure environment. The financial consequences of every second of the outage may increase the pressure.

To ensure the team’s well-being under such circumstances, a structured preparation is required. This may involve the following aspects:

- Social
- Etiquette
- Emotional 
- Equality 
- Source of truth 
- Blame handling

See Chapter 9, extremely large Table 9.19 Aspects to Ensure the Well-Being of Incident Response Teams 

In fact, coordinating complex incidents every time with a new, dynamically allocated team is a dynamic reteaming exercise of sorts that incident coordinators need to master. 

Incident response teams are the opposite. By definition, they are dynamic and short- lived. The differences between development and incident response teams are summarized in the table below: 

| Characteristic | Development Teams | Incident Response Teams |
|----|----|----|
| Working Hours | Business Hours | 24/7 |
| Regular daily number of working hours | 8 | Defined? |
| Teams dynamically formed for a short-lived mission | No | Yes |
| Teams disband afer fullfilling a short-lived mission | No | Yes |

### 9.4 Incident Postmortems 
For an incident postmortem to be effective, its value needs to be greater than the time investment to conduct it. Although this ratio is difficult to calculate quantitatively, a qualitative assessment may be possible.

- According to PagerDuty, “A postmortem (or post-mortem) is a process intended to help you learn from past incidents. It typically involves an analysis or discussion soon after an event has taken place.”

- According to OpsGenie, “A postmortem is a written record of an incident that contains information such as incident impact, mitigation steps, root cause, and follow-up actions. The goal of a postmortem is to understand all root causes, document the incident for future reference, discover patterns, and enact effective preventative actions to reduce the impact or likelihood of recurrence.”

- The original Google SRE book Site Reliability Engineering: How Google Runs Production Systems states, “A postmortem is a written record of an incident, its impact, the actions taken to mitigate or resolve it, the root cause(s), and the follow-up actions to prevent the incident from recurring.”

#### 9.5 Effective Postmortem Criteria 
Refer to full Table 9.21 Effective Postmortem Criteria

- Summary of table: 

| Criterion | Explanation |
|----|----|
| Learning | The value of an incident postmortem is in the learning it generates. The learning can take different flavors. On the one hand, direct action items to fix immediate issues represent one-time learning episodes. On the other hand, there are a number of additional opportunities beyond the immediate action items to inject learnings into the product delivery organization. |
| Record | A written record of a postmortem is required for future reference to enable learning for people who did not take part in the postmortem meeting. Clear technical writing is essential to motivate the people to read and learn from a postmortem that was conducted by others. Opaque and unstructured postmortems will not be read and learned from, which devalues the process to nearly zero. |
| Actions | Clearly defined action items are an essential part of incident postmortems. Each action item needs to have a driver. Being a driver may mean to work on the action item directly or it may mean to orchestrate the work of others on different parts of the action item. Moreover, each action item needs to have a review date. On that date the driver of the action item, the incident coordinator, and, if necessary, an agile coach should review the progress achieved so far. If the action item is not yet done, they should set a new review date. |

#### 9.5.1 Initiating a Postmortem
Postmortems need to be initiated by a role in the incident response process that has the respective responsibility.

The incident communicator only takes part in incidents with severity “critical.” If no incident communicator was part of the incident, the incident coordinator needs to either take care of the postmortem record or ask someone to do so. For instance, an agile coach may support the incident coordinator in this regard.

Generally, the availability of an agile coach in the postmortem is beneficial for several reasons. An agile coach can help

- Create the incident record using different media (writing, video, audio)
- Bridge what happened during the incident with overall organizational processes and practices
- Ensure proper handling of the postmortem action items in the work item management tool
- Follow up on the postmortem action items 
- Identify common themes across postmortems 

The incident coordinator needs to clarify the repsonsibilites of an agile coach when inviting them to the incident postmortem. 

Initiating a postmortem is not necessary for every incident. The incident response process needs to clearly define incidents that require an incident postmortem to be conducted.

#### 9.5.2 Postmortem Lifecycle
After the decision to initiate a postmortem is made, the postmortem lifecyle begins. 

Postmortem Lifecycle Activities 

- Before Postmortem 
    - Invite participants
    - Clarify responsibilities
    - Construct the timeline 
    - Run automated incident conversation analysis
    - Create an initial postmortem write-up
    - Clarify people issues 

- During Postmortem 
    - Establish the Prime Directive
    - Clarify responsibilities
    - Refine the timeline 
    - Review the timeline 
    - Derive immediate action items 
    - Derivce action items for improvements in broader processes and practices 
    - Prioritize action items
    - Assign action items
    - Agree on review dates for action items
    - Agree on forums where the postmortem needs to be presented and by whom
    - Solicit quick feedback on postmortem effectiveness  
- After Postmortem
    - Create or complete work items for action items in the work item management tool
    - Follow up on action items line with agreed review dates
    - Present the postmortem
    - Finish the postmortem write-up
    - Upload the postmortem video recording, if any
    - Upload the postmortem audio recording, if any
    - Distribute the postmortem content
    - Solicit periodic feedback on the outcoumes achieved through the postmortem 

#### 9.5.3 Before the Postmortem
The first activity before the postmortem begins is to invite the necessary participants to the post- mortem meeting in a timely fashion for a suitable time frame. Once they are invited, the incident coordinator needs to clarify responsibilities by postmortem phase so that each participant knows in advance what to do before, during, and after the meeting.

- Reconstructing the Timeline: One of the major activities before the meeting is the reconstruction of the postmortem timeline. This can initially be done by the incident participants working individually on a shared timeline. Later the reconstructed timeline will be refined and discussed jointly in the postmortem meeting. The incident coordinator needs to request the incident participants to work on the timeline reconstruction before the meeting.

- Having Conversations Analyzed: Timeline reconstruction can also be supported by having the human conversations in the chat management tool, by email, and in the online video conferencing tool analyzed automatically.

- Drafting the Postmortem Write-Up: Before the postmortem, the incident coordinator needs to ask the person responsible for the postmortem write-up to draft itinitially. The draft needs to be started at the agreed postmortem location (e.g., on-call management tool, SRE wiki, source control repository, etc.).

- Taking Care of People Issues: Interpersonal issues that surfaced during the incident need to be handled with the utmost of care. It is critical that these issues are taken care of before the postmortem meeting. This is so important that an already planned postmortem meeting should be delayed if known interpersonal issues have not been clarified yet. This is because making angry people with grudges against each other talk about what happened publicly in front of other people might escalate, become very emotional, and even derail the entire postmortem meeting.

#### 9.5.4 During the Postmortem 

Once the pre-postmortem activities are finished, the postmortem meeting can begin in a well- prepared manner. If possible, the meeting should be recorded in full. The incident coordinator should open the meeting with a greeting and a heartfelt thank-you to everyone for detecting, tackling, and resolving the incident. Right after that, the incident coordinator should explain the agenda points of the meeting to put everyone on the same page about what the team will be doing in the course of the meeting.

- Prime Directive: The first point on the agenda needs to be to put the participants in the right mindset. The right mindset needs to be blameless at the core. “We are not here to blame each other” is the message the incident coordinator must convey.

- Reviewing the Timeline: The next big point on the agenda declared by the incident coordinator is to refine and review the timeline, ensuring that it reflects everyone’s views on what happened and in which order. Before starting, the incident coordinator needs to reiterate the responsibilities that were distributed before.

Review the following: 
- Do you think the incident priority was set to the correct value? 
- Do you think the incident severity was set to the correct value? 
- Is this the best visualization of the data to illustrate the point? 
- Can the visualization be understood by people who did not take part in the incident? 
- Are the log queries for the visualizations shown stored and linked from the write-up? 
- Will the majority of people have access to the queries? 
- Should this passage go into the external write-up of the postmortem? 

- Generating Action Items: Once the timeline has been refined and reviewed, it is time to generate the action items. A good starting point for action item generation are the corresponding side notes that were made as bullet points during the timeline discussion.

- Checklist to assist generating action items during a postmortem
    - Incident Response Process
        - Does any runbook need to be updated? 
        - Does the on-call training need to be updated? 
        - Does the on-call rotation setup need to be updated? 
        - Does the incident classification with priorities and severities need to be updated? 
        - Does any SLO need to be updated/added/removed? 
        - Does any SLI need to be updated/added/removed? 
        - Does any stakeholder notification need to be updated/added/removed
    - SRE Infrastructure
        - Does any dashboard need to be udpated/added/removed?
        - Does the alerting algorithm need to be updated? 
        - Does the tool chain need to be updated? 
        - Does the SRE wiki need to be udpated/extended? 
    - Architecture
        - Is there a dependency between services that can be loosened? 
        - Does an aspect of architecture governance need to be updated/introduced? 
    - Organizational
        - Does any responsibility need to be made clearer? 
        - Does the organizational structure need to be updated? 
        - Does the employee onboarding program need to be updated? 
        - Does the workload need to be reduced to avoid burnout of some people? 
    - Collaboration
        - Are there interpersonal issues to be solved preventing collaboration? 
        - Do the collaboration practices between departments need to be updated? 
    - Customer support
        - Does the interaction between the first level support and the customers need to be updated? 
    - Hiring
        - Does the list of skills required for a particular role need to be updated? 
        - Does the list of technologies required for a particular role need to be updated? 
    - Procurement
        - Does the list of supplier selection criteria for custom software development need to be updated? 
        - Does the list of supplier selection criteria for software components/services need to be updated? 

- Postmortem distribution: One of the final steps in the postmortem meeting is to decide how the postmortem learnings should be distributed and by whom. The incident coordinator, agile coach, and incident participants spent quite some time learning from the incident and identifying improvements across many dimensions to act on the learnings. Now is the time to distribute the learnings throughout the organization in an efficient and effect

#### 9.5.5 After the Postmortem
Once the postmortem meeting is over, the action items contain a clear path to further action. First, the action items in the work item management tool need to be checked for completeness. In all likelihood, not all the details were spelled out clearly enough during the postmortem meeting for the description to be understood thereafter by people who did not take part in the meet- ing. The action item descriptions in the on-call management tool need to be completed immediately after the meeting, while the conversations and context are fresh in the minds of the action item drivers. The action item drivers should take care of this.

#### 9.5.6 Analyzing the Postmortem Process
Running the process takes time and effort. Analyize the effectiveness to get an understanding of the outcomes achieved through the process. Drive postmortems to get improvement. 

- Action Item Lead Time and Cycle Time: Your item management tool, for example; Jira will handle calculations of lead time or this will be discussed during Sprint planning

- Content Consumption Statistics: The content is produced by the postmortem participants to be used by others in the product delivery organization. That is, content consumption indicates whether the usefulness of the postmortem process goes beyond the immediate postmortem participants, their teams, and the teams affected by the postmortem action items. It indicates whether the quality and attractiveness of the postmortem content are high enough for teams not affected by the incident to take notice and start learning from other peoples’ service outages.

- Soliciting Feedback on Outcomes: Another way to analyze the postmortem process is to solicit feedback on whether the postmortem activities yield real outcomes. The feedback can indicate whether some of the outcomes achieved by the teams are materializing through application of the postmortem process; that is, whether the outcomes materialize through processing the postmortem action items in a reasonable time frame and feeding the postmortem learnings into the right processes and groups in the product delivery organization. If not for the postmortem process, the outcomes would probably not materialize or would materialize much later, or it would be much more difficult to bring them about.

#### 9.5.7 Postmortem Template
See Chapter 9 for template

#### 9.5.8 Facilitating Learning from Postmortems
The previous sections showed the importance of learning as the central theme for the relevance of postmortems. Who needs to learn what, when, and how should be on top of agile coaches’ minds when attending postmortem meetings. This thought process yields action items for vari- ous teams and groups in the product delivery organization.

In addition to that, the agile coaches can sift through the postmortems and discover patterns. Common themes can be found that come up again and again in different situations, with different teams and services. Tackling the common themes might require some bigger initiative to be started and executed throughout the organization.

Initiatives like that are home turf for agile coaches. They know how to pull the strings in the organization to convince the decision makers, get the ball rolling, and roll out a change in many teams within a reasonable amount of time. Following are some examples of such initiatives.