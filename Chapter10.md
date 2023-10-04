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
When defining the consequences for conditions governed by an error budget policy, an attempt should be made to define them in an automatable and traceable manner, if possible. Doing so will enable automated checks whether or not the consequences are executed as agreed.

To be sure, error budget policy consequences will contain lots of qualified statements to be interpreted by humans. However, wherever possible, automatable and traceable clauses should be defined to enable automated analysis.

The error budget depletion consequences may be categorized. The following categories might be useful:

- Assigning people
- Conducting activities
- Stopping activities

- Example Error Budget Policy Consequences

| Consequence Category | Example Consequences |
|----|----|
| Assigning People | <ul><li>Assign a certain percentage of engineers on the team to reliability work until certain conditions apply</li><li>Escalate to a higher-up to influence the assignment of engineers to reliability work</li></ul> |
| Conducting Activities | <ul><li> Conduct a postmortem</li><li>Create an action item</li><li>Prioritze an action item in a certian way</li><li>Get an action item done within a certain amount of time</li><li>Engage with the owner of a dependent service (internal team or external company)</li><li>Communicate the error budget state to certain parties</li></ul> |
| Stopping Activities | <ul><li>Stop new feature releases to the staging environment</li><li>Stop new feature releases to the production environment</li></ul> | 

### 10.6 Error Budget Policy Governance 
The cross-product of policy conditions and consequences yields the overall set of actions governed by the error budget policy. The more data-driven the conditions and consequences can be, the more traceability and transparency can be associated with a given policy. 

The error budget policy consists of conditions and consequences. Further, it has some level of traceability. The conditions can be triggered either automatically or manually. Likewise, the consequences can be executed using either automated or manual runbooks. The resultant traceability will be a combination of automated and manual steps providing transparency.

- Example Error Budget Policy Clause 

| Condition | The error budget for dead letters in the message queue "data_inflow" is exhausted permaturely before the end of the current error budget period. | 
| Automated Trigger | An alert is sent to the people on call when the error budget is exhausted before the end of the current error budget period. | 
| Consequence | <ul><li> Raise an action item to be prioritized at the top of the team backlog</li><li>Link the action item to the error budget policy</li><li>Finish the work on the backlog item within a week</li></ul> |
| Automated Runbook | The consequence is partly coded up in an automated runbook. The action item is created and linked to the error budget policy automatically. The people on call need to get the action item prioritized | 
| Traceability | <ul><li>Check for work items in the work item management tool linked to the error budget policy</li><li>Check the action item lead time</li></ul> | 

### 10.7 Extending the Error Budget Policy
The conditions in an error budget policy should ideally be expressed in terms of error budget depletion. However, if a team wants to deviate from that, they should be free to do so. It is more important to have an error budget policy in place that is working effectively based on conditions expressed using means other than functions of error budget depletion than it is to have no error budget policy at all. Even worse is to have an error budget policy that does not get enacted. This is because in that case, the time taken by many people to agree on the policy was fully wasted.

The need for policy conditions to be specified not just as functions of error budget depletion may stem from the fact that the team may have resource-based alerts—for example, “CPU is over 80%” or “Memory is over 90%”—in addition to SLOs. The SRE infrastructure might not yet support all the necessary SLIs or ways to measure existing SLIs to express every reliability concern of every service in the product delivery organization. Therefore, some resource-based alerts might still be there to fill in the gaps.

Following this, the error budget policy might contain conditions that are rooted in resource-based alerts. For example, such conditions might be:

- High CPU consumption over extended time periods
- Sudden increase in dead letters in dead letter queues
- Sudden active message count increase in message queues
- High background job restart numbers

What is more, the teams might specify additional points in an error budget policy that only seem distantly related at first. For example, a team might list phases in the release lifecycle and specify different error budget policies by phase. This might happen when each phase takes a significant amount of time because the team’s production release cadence is rather infrequent. Often in this context, many teams release to production together at the same time

- Example Release Lifecycle Phases and Their Durations 

| Release Lifecylce Phase | Possible Duration | 
|----|----|
| Planning | Several days |
| Development | Several months |
| Rollout to staging | Several days | 
| Testing for regulatory compliance | Several days to several weeks |
| Hotfix rollout to all production environments | Several days |
| Feature release rollout to all production environments | Several weeks |

For instance, the teams in the product delivery organization might plan releases using so- called Program Increment (PI) plannings as suggested by the Scaled Agile Framework (SAFe3). In this case, the teams might also be organized in so-called Agile Release Trains (ARTs) as suggested by the framework. Given this, a PI planning includes all members of all teams belonging to an ART. The planning is executed like a conference that runs for several days. During that time, all the team members are expected to focus on the planning activities. It follows that the teams might want to specify the policy conditions in their error budget policies that specifically apply during the PI planning.

This might sound counterproductive. The error budget policy should govern the team’s actions to ensure reliability in production regardless of the release lifecycle phase. After all, there is always a previous release running in production whose reliability has to be ensured. Why on earth would any other activity, like PI planning, have an influence on ensuring reliability in pro- duction according to the error budget policy?

### 10.8 Agreeing to the Error Budget Policy 
The operations engineers, developers, and product owner of a team need to agree on the error budget policy, as do the people who are specified in the escalation policy to break ties in case of disagreements. It is beneficial to drive this agreement in stages to involve the right people at the right time for the appropriate amount of time. Agreement can be staged in the following way.

1. The operations engineers and develops create an error budget policy draft using their technical knowledge. 
2. The product owner gets involved to review the error budget policy draft from the user and business point of view. 
3. The people specified in the escalation policy get involved to review the error budget policy from teh clarity, specificity, precision, and data-drive measurements point of view. 

The SRE coaches should initiate and drive process. First, they should invite the operations engineers and developers for the services in the scope of the error budget policy for a discussion rooted in the services’ past incidents and bigger outages. The discussion will be fairly technical. At the beginning of the discussion, the SRE coaches should reiterate the context and motivation and explain how the discussion will be facilitated.

The SRE coaches should pay close attention to the influence on the team exercised by other frameworks and methodologies to learn some specific aspects and use the learnings in error budget policy discussions with other teams. Moreover, these aspects provide a good basis for discussions with agile coaches to drive broader organizational improvements.

The SRE coaches should see the discussion converge by achieving agreement on the error budget policy draft by the operations engineers and developers. Once this agreement has been reached, the SRE coaches should invite the product owner to the discussion of the draft.

At this point, the technical discussions are over, the conditions addressed by the error budget policy are clear, and the corresponding consequences are defined. The product owner can now review the current error budget policy draft from the customer and business point of view. That is, does the error budget policy strike a good balance between the reliability work and the new feature work to provide an optimal user experience and business benefit? Does it dictate that the team should work on reliability when required to ensure a good user experience for existing features? Does it allow the team to work on new features when the reliability of existing features is up to standard? These checks by the product owner also contribute to the error budget policy being written in a way that can be understood by people without deep technical expertise. This is especially required by the people specified in the escalation policy.

### 10.9 Storing the Error Budget Policy
Generally speaking, an error budget policy is a team-specific document. However, it might be beneficial to store it publicly. For example, a section in the SRE wiki might be a good place to store the error budget policies of all teams in a transparent manner. Storing the policies publicly has several advantages.

- Having an effective error budget policy is an advanced SRE practice. Therefore, it may take a long time for teams to start adopting it. For the same reason, there are not a lot of examples on the web to learn how an effective error budget policy can be created. Being able to learn from other teams in the product delivery organization by analyzing their policies is a great catalyst for other teams to adopt the concept.
- During postmortems, when several teams are involved in an outage, it is beneficial to enable the postmortem participants to look up the error budget policies of the involved teams in parallel. This might generate new postmortem action items to adapt existing policies. The process might also prompt the creation of a new error budget policy for a team that does not yet have one in place.
- People specified in the escalation policy approving a team's error budget policy need easy access to it. Furthermore, these stakeholders may need to approve the error budget policies of several teams. For example, a VP of engineering may be on the escalation policy list of several teams’ error budget policies. Such stakeholders would prefer a central location for all the error budget policies from all teams they are involved with.

In terms of the storage medium, storing the error budget policy in a source-controlled wiki may be a good option. It combines the transparency of a changelog with the ease of editing a wiki. Additionally, if an error budget policy is stored on a wiki page within a larger application lifecycle management system, the work items linked to the wiki page may be displayable on the page automatically along with details such as their state, last update date, and owner. This con- tributes to an additional degree of transparency as to whether the conditions and consequences, which can be expressed as work items, are executed as stated in the policy.

### 10.10 Enacting the Error Budget Policy
Once the error budget policy is agreed, the SRE coaches should invite the team for an explicit kick-off to enact it. This is because it is fairly easy for an error budget policy to remain a docu- ment that gets forgotten as the day-to-day work takes over people’s attention.

The team should decide on the date of the enactment. From that date onward, the error budget policy governs decisions about reliability work prioritization in the team. The date should be chosen in such a way that automatic policy checks that are feasible are set up beforehand.

This means that all the conditions and consequences from the error budget policy that lend themselves to automatic processing should be set up to be triggered and executed in an automated fashion. This may include setting up new alerts in the SRE infrastructure and noti- fications in the on-call management tool. Furthermore, it may include setting up automated runbooks in the on-call management tool. As part of the process, new feature requests to the SRE infrastructure may be raised to increase the degree of automation in the future.

The team needs to check the next error budget policy review date and update it as needed. How an error budget policy review can be done is the subject of the next section.

### 10.11 Reviewing the Error Budget Policy
It is beneficial to run error budget policy reviews in the form of retrospectives. This is because retrospectives provide a structured way to solicit process feedback in a short time frame without lots of preparation. This is exactly what is needed in an error budget policy review. The review is not only about sharpening the defined clauses. To a greater degree the review is about finding out whether the defined error budget policy is effective in that it delivers outcomes in terms of reliability work prioritization.

Running a retrospective well and in a professional manner is the home turf of agile coaches. Therefore, it is great to engage an agile coach to run an error budget policy review as a ret- rospective. The agile coach should invite the people who agreed on the policy and the people who were going on call for the services under the policy since the last retrospective. The invitation should be sent about two weeks before the actual retrospective to accommodate people’s schedules.

In the retrospective, the effectiveness of the error budget policy should be discussed. The following questions may guide the discussion. 

- Does the error budget policy get enacted at all? 
    - If the error budget policy does not get enacted, what could be the reasons for that? For example, ar the triggers for enacting the policy automated as much as possible? 
    - If the error budget policy does get enacted, is it transparent? 
- Are the conditions specified to trigger the error budget policy appropriate? 
- Are the consequences specified for each condition executed as envisioned? 
- What are the outcomes of the application of the consequences? 
    - Does reliablity work prioritization happen as intended? 
    - If so, does the prioritization lead to reliability improvements? 
- Do the conditions and consequences need any updates? 
    - Create new conditions/consequences
    - Update existing conditions/consequences
    - Delete existing conditions/consequences

The retrospective should define action items to improve the policy based on the discussion in the meeting. Importantly, it should define who will update the actual error budget policy, how the update will be communicated, and to whom.

### 10.12 Related Concepts 
There are a number of additional concepts that might be useful in the context of error budget policies. They can be found in the literature and in online articles. In this section, an overview of the concepts is provided to establish a more comprehensive view of the current state of thinking in the area of error budget policies. 

- Additional Concepts in the Context of Error Budget Policies

| Concept | Explanation | 
|----|----|
| Code Yellow | At Google, a state of Code Yellow can be declared. It means that everyone affected needs to stop working on features and start working on reliability. Code Yellow is applied during the teams’ business hours. In an error budget policy, declaring Code Yellow can be specified as a consequence for a condition. Specifying Code Yellow in the error budget policy has the advantage that the exit criteria from that working mode are automatically specified by the condition that triggered it. When the condition does not apply anymore, the Code Yellow working mode does not apply either. |
| Code Red | LinkedIn also has a state of Code Yellow. In addition, it has a state called Code Red. Code Red is Code Yellow applied around the clock. That is, declaring Code Red means that everyone affected needs to stop working on features and start working on reliability around the clock. Code Red can be specified as a consequence in an error budget policy. |
| Silver Bullet | In Implementing Service Level Objectives, the concept of a silver bullet is introduced. It applies when the error budget policy specifies that new feature releases are prohibited until there is a certain level of error budget available again. In this case, there may be an agreement in the error budget policy to have a certain small number of silver bullets available per year (e.g., three). The business can use the silver bullets to allow a new feature release despite the policy forbidding new feature releases. When the agreed number of silver bullets is used within a year, the business cannot lift the ban on new feature releases. |
| Thaw tax | Implementing Service Level Objectives2 also introduces the concept of thaw tax. Thaw tax also applies when the error budget policy declares a ban on new feature releases. It works as follows. For every day a new feature release was done despite the fact that the error budget policy declared a ban on new feature releases, a daily thaw tax is added to the day. So, for each day that violated the ban, the number of ban days gets increased by 1 + thaw tax. The thaw tax is defined in the error budget policy and is designed to extend the time when only reliability work is allowed in case of error budget policy violations. For example, imagine the thaw tax is agreed to be half a day. Further, imagine the error budget policy declared a ban on new feature releases as a consequence to a policy condition. The condition gets fulfilled, and the ban on new feature releases gets declared. During the ban, three new feature releases are done on three different days. For each day, the thaw tax of half a day is added. This means that each day now counts as 1 day + 1⁄2 day thaw tax = 1.5 days. Thus, for three days when new feature releases were done despite the ban, 3 x 1.5 = 4.5 days of ban time are added. During these days, only reliability work is allowed. | 
| Error Budget top-up | Nobl9 applies a concept of error budget top-up to situations in which a team’s error budget depletion is found to be due to the team’s external dependencies. The dependencies can be in another team’s services within the same product delivery organization or in external companies’ services. So, when a team depletes some error budget that is then attributed to its external dependency, the lost error budget is topped up. No further details of the concept are provided by Nobl9. However, the error budget top-up needs to be done within the current error budget period. Otherwise, hoarding of the error budget will take place, which does not reflect the number of errors allowed by the respective SLO. |

The SRE coaches need to assess whether it would be beneficial to introduce and realistic to execute any of these concepts in a given product delivery organization. Code Yellow and Code Red would require an organization-wide agreement. Once declared, it applies to all the affected teams. This means a team’s error budget policy containing a Code Yellow or Code Red consequence may have an influence on other teams. The other teams need to be prepared to work according to the Code Yellow or Code Red working mode based on another team’s error budget policy.

The silver bullet, thaw tax, and error budget top-up concepts can be applied within the context of a team. The silver bullet and thaw tax require some transparent means to keep the current score. Questions like “How many silver bullets are left within a year?” and “How many thaw tax days were added last month?” must be answerable in a self-service manner to cater to full transparency.

The error budget top-up concept requires the corresponding SRE infrastructure to be able to make the top-ups with precision.

--
EoF