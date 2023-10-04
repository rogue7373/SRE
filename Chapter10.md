# Chapter 10 - Setting Up an Error Budget Policy
A team’s error budget policy can be defined only after solid basic SRE foundations are in place that is, the SLOs have been defined, the SLO breaches have been analyzed, and the SLOs have been adapted several times based on ongoing analysis of the SLO breaches.

### 10.1 Motivation
Once a solid SRE foundation is in place, it is time to start discussing the error budget policies. The team might think SRE is fully established and no further refinement is needed. Therefore, it might require effort for the SRE coaches to motivate the team to optimize the established SRE practice in the form of an error budget policy.

How would the introduction of an error budget policy mature the SRE practice in a team?

- By formalizing the consequences of breaching SLOs in terms of engineering capacity allocation to reliability. 
- Strike an agreement between the operations engineers, developers, product owners, and some management stakeholders about when and to what extent the team's capacity should be dedicated to reliability work. 

The argument is that it does not make sense to add new features to a service in which existing features do not run reliably. The authors argue that halting new feature releases of services until they are within their SLOs leads to a big rush of new feature releases later. Once the services are brought within the SLOs, every team is pushing many new features at once. This snowballs into a large number of changes in production, all done within a very short period of time. In turn, this greatly increases the likelihood of failures and, therefore, of premature error budget exhaustion. In fact, it might make a product delivery organization that usually releases software in small batches release software in a way similar to a giant release of a monolith.

- These different views on what the error budget policy should contain demonstrate that an error budget policy should be crafted carefully, individually, and on a team-by-team basis.
- The policy should reflect the views of operations engineers, developers, and the product owner. It should guide data-driven decision-making regarding reliability investments and time allocation to reliability work in the respective team.

- With an error budget policy, the team takes a longer-term view of reliability that goes beyond immediate fixes of individual SLO breaches and incident resolutions. 

The goal of the error budget policy is to make definitions, reach agreements, and stipulate action to support two principles from Google’s Site Reliability Workbook:

- "Manage by service level objectives (SLOs)"
- "SRE needs SLOs with consequences"

The error budget policy is, indeed, about defining the consequences that will have a noticeable and transparent effect on the engineering capacity allocation to reliability within the product delivery organization.

> Key Insight: An error budget policy is about defining consequences of breaching SLOs that will have a noticeable and transparent effect on the engineering capacity allocation to reliability within the product delivery organization.

### 10.2 Terminology 
Achieving meaningful error budgets in a team requires looking at error budget depletion graphs to see which SLOs are broken so frequently that their corresponding error budgets get depleted prematurely. Premature error budget depletion is a matter of definition. It may be defined to mean error budget exhaustion before the end of an error budget period, or it may be defined to mean a high speed of error budget depletion within a given time frame (e.g., 50% of a monthly error budget depleted within a week). Other definitions are also possible.

- SRE Cheat Sheet: 

| Term | Definition | 
|----|----|
| Error budget grant | The error budget afforded by the SRE infrastructure based on an SLO. Once it is granted, the infrastructure keeps track of the remaining error budget based on the occurring SLO breaches. |
| Error budget period | A fixed period of time for which the SRE infrastructure grants an error budget | 
| Error budget grant period | Same as error budget period | 
| Error budget depletion | The consumption of error budget. Each SLO breach depletes a small bit of the error budget | 
| Error budget exhaustion | the depletion of the error budget to zero | 
| Premature error budget depletion | The depletion of the error budget to an agreed level before the end of an agreed period. For example, the agreed error budget level can be 10% or 50%. The agreed period can be the entire error budget period of four weeks or just one week. Following this, premature error budget depletion can be defined as 90% of the monthly error budget depleted within four weeks, or 50% of the monthly error budget depleted within one week. | 
| Premature error budget exhaustion | The depletion of the error budget to zero before the end of an agreed period | 
| Error budget policy | An agreed document stating what the team will do in terms of reliability work prioritization in case of premature error budget depletion |

### 10.3 Error Budget Policy Structure 
An error budget policy needs to be structured well so that readers quickly understand the agree- ment to prioritize reliability work over other work in a team. To provide this structure, an error budget policy template can be defined in the product delivery organization.

The error budget policy template needs to specify the required parts of an error budget pol- icy and leave enough room for additional freeform specifications to provide a good degree of freedom to the teams for expressing their prioritization of reliability work. Table 10.1 summarizes the required parts of an effective error budget policy.

- Error Budget Policy Parts 

| # | Part | Explanation |
|----|----|----|
| 1 | Scope | What are the services in scope for the error budget policy? |
| 2 | Purpose | What is the purpose of the error budget policy? |
| 3 | Conditions | What concrete conditions require the error budget policy to be enacted? | 
| 4 | Consequences | What are the concrete consequences to be drawn for each condition where the error budget policy applies? |
| 5 | Escalation Policy | In case of disagreements about conditions, actions, and reliability work prioritization in general, who will break the ties and how? |
| 6 | Agreed by | Who was involved in the error budget policy agreement? | 
| 7 | Next review date | When will the error budget policy be reviewed next? |

The scope of an error budget policy is typically all the services owned by a team. As such, defining the scope usually does not involve extensive discussions. This is different for the error budget policy purpose. It may take a while to clarify and agree on its purpose. The SRE coaches should steer the discussion toward the key insight that an error budget policy is fundamentally defined in order to influence the prioritization of reliability work in the team: that is, the consequences of insufficient reliability using directions for reliability work prioritization.

Often, an engineering manager or operations manager would be defined as the go-to person to break ties as part of the error budget policy’s escalation policy. At times more senior people in a product delivery organization, such as a vice president of engineering, vice president of operations, or CTO, might be more appropriate. The scope of the error budget policy should inform the designation of the most relevant tiebreaker.

- The escalation policy may also outline a procedure for breaking ties.

> Example: For example, the SRE practice at Google is set up in such a way that the people with the role “SRE” can refuse the responsibility for services that consistently violate their error budgets. In this case, the responsibility is handed over to the development teams that own the services. A detailed description of such a procedure needs to be made in the escalation policy part of the error budget policy.

### 10.4 Error Budget Policy Conditions
The previous section introduced the specification of the error budget depletion conditions and consequences that should be at the heart of an effective error budget policy. The conditions can be categorized as follows:

- Error budget spend
- Error budget burn rate
- Dependency handling 

- Example Error Budget Policy Conditions

| Condition Category | Example Conditions | 
|----|----|
| Error budget spend | <ul><li> Premature error budget exhaustion before the end of the current error budget period</li><li>A certain percentage of the error budget depleted in the current error budget period</li><li>A certain percentage of the error budget in the current error budget period depleted by a single incident</li><li>A certain percentage of the quarterly error budget depleted by a certain type of outatge</li></ul> | 
| Error budget burn rate | <ul><li>A certain percentage of the error budget granted for the current error budget period depleted within 24 hours</li><li>A certain percentage of the error budget granted for the current errror budget period depleted wihtin seven days</li></ul> | 
| Dependency handling | A certain percentage of the error budget granted for the current error budget period depleted due to failures in a dependent service |

### 10.5 Error Budget Policy Consequences

