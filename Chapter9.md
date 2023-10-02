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


