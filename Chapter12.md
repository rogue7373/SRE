# Chapter 12 - Implementing Organizational Structure
The SRE practice achieved so far fulfills the promise of the SRE transformation in that it enables the product delivery organization to operate software reliably at scale. The SRE practice can be introduced without reorganization or the introduction of new formal roles. This is the right strategy, as it allows the organization to find its way of practicing SRE through experimentation, working collaboratively across existing organizational boundaries. 

Thinking about the organizational structure before experimenting with SRE would require the organization to make decisions that would be difficult to change later without the necessary practical SRE experience. However, once the SRE practice has been proven effective through experimentation and is on the way to becoming solidified, questions regarding the right organizational structure to support and sustain SRE over the long term need to be considered.

- Questions Driving SRE Organizational Structure 

| Category | Questions | 
|----|----|
| Roles and Responsibilities | <ul><li>What are the responsibilities in the realm of SRE?</li><li>What are the roles in the realm of SRE?</li><li>What are the necessary skills by role?</li><ul> |
| Business Vision | <ul><li>What are the long-term business goals with SRE?</li><li>What is the long-term vision for the SRE transformation?</li><li>Is ROI expected for SRE activities?</li></ul> | 
| Leadership | <ul><li>What kind of leadership is needed for SRE?</li><li>Is business/product/technical leadership needed?</li><li>Is a new C-level leader needed?</li></ul> |
| Career | <ul><li>What are the career paths by role in the realm of SRE?</li><li>How do you attract people to SRE from inside and outside the organization?</li><li>How do you switch to an SRE career from another role</li></ul> |
| Organizational | <ul><li>What should be the organizational visibility of SRE?</li><li>Should SRE become a new dedicated organizational unit?</li><li>What are the reporting lines by role in the realm of SRE?</li><li>What should be the formal authority by role?</li><li>What should be the formal power by role?</li><li>How do you measure the success of SRE?</li></ul> | 
| Budget | <ul><li>Should SRE get its own dedicated budget?</li><li>Who should be responsible for the budget?</li><li>Who should be repsonsible for budget distribution?</li><li>What are teh salaries by role and location in the realm of SRE?</li></ul> |
| Planning | <ul><li>How many people by role would be needed in the realm of SRE in the next one to three years?</li><li>Where in the world would the poeple need to be hired?</li><li>Is fully remote work acceptable by role?</li></ul> |
| Regulatory | <ul><li>How formal is the SRE practice?</li><li>Can SRE be used for auidit purposes?</li><li>Does SRE help fulfill regulations for software operations?</li></ul> |
| Decision-making | <ul><li>Which organizational decisions should be governed by SRE?</li><li>Which organizational decisions should be supported by SRE?</li><li>Which organizational decisions are out of scope for SRE?</li></ul> |

These quesitons are multidimensional and have wide implications on organizational structure, budget distribution, and people's career. Therefore, it is important to deliberately start discussing het questions late in the SRE transformation journey, once the organization is practicing SRE successfully. 

### 12.1 SRE Principles Versus Organizational Structure
The SRE principles from the Site Reliability Workbook

1. Operations is a software problem
2. Manage by service level objectives(SLOs)
3. WOrk to minimize toil
4. Automate this year's job away
5. Move fast by reducing the cost of failure
6. Share ownership with developers
7. Use the same tooling, regardless of function or job title.

Additionally, there are three more principles for practicing SRE

1. SRE needs SLOs with consequences
2. SREs must have time to make tomorrow better than today
3. SRE teams have the ability to regulate their workload

When looking at the principles, an important aspect to notice is that the organizational structure for implementing SRE is not on the list. This means the SRE principles can be implemented by software delivery organizations using different organizational structures.

It follows that a discussion about a suitable organizational structure needs to be led separately from the SRE principles. The organization needs to fulfill the SRE principles using an organizational structure that suits it. Fulfillment of the SRE principles comes first; the organizational structure to do so is secondary.

> <b>SRE Myth:</b> SRE can only be done with central SRE Team

> <b>SRE Myth:</b> A dedicated SRE team is required to do SRE

By contrast, does the organizational structure influence the fulfillment of the SRE principles? It does, indeed! The organizational structure certainly steers how people work together. For some, it simplifies collaboration and communication; for others, it impedes it. The influence is highly dependent on the organization and the people who work there.

### 12.2 Who Builds It, Who Runs It? 
The title of this section is inspired by the line expressed by Amazon CTO Werner Vogels in an interview for ACM Queue from 2006: “You build it, you run it. This brings developers into contact with the day-to-day operation of their software. It also brings them into day-to-day contact with the customer. This customer feedback loop is essential for improving the quality of the service.”

> You build it, you run it

The above statement is a way to give the repsonsibility for running the services to those who build them; that is, the development teams themselves. This maximizes the incentives for the development teams to invest in reliability. 

#### 12.2.1 "Who Builds It, Who Runs It? Spectrum 
“You build it, you run it” describes one end of the “who builds it, who runs it?” spectrum. At the other end is the opposite way of running services. It can be referred to as “you build it, ops run it.” The phrase was probably coined by Steve Smith in a blog post with the same name, as part of the “Who Runs It” blog post series. With “you build it, ops run it,” the development teams are responsible for building services and the operations teams are responsible for running them in production. The development teams are not directly incentivized for implementing reliable services. This is because they do not go on call for their services running in production. This responsibility is fully with the operations teams.

In addition to the "you build it, you run it" option two additional options are: 

- "You build it, you and SRE run it"
- "You build it, SRE run it" 

With “you build it, SRE run it,” a dedicated SRE team is established. It is staffed with people who possess development and operations knowledge. That is, they can develop services like developers and operate them like operations engineers with a software development background. The development team builds the services and the SRE team runs them. For the SRE team to take a service into operation the service needs to fulfill strict reliability criteria. Also, once the SRE team is operating the service, the reliability criteria need to stay fulfilled. If the service consistently fails to stay within its error budgets, the SRE team returns the service to the development team, which then has to run the service until service reliability is reinstated.

#### 12.2.2 Hybrid Models
Beyond the options above, some additional hybrid models are possible: 

- "You build it, ops sometimes runs it"
- "You build it, you run it but some specific use cases are additionally monitored by ops"
- And others 

The “you build it, ops sometimes run it” model is described in a blog post6 of the same name. It is a combination of the “you build it, you run it” and “you build it, ops run it” models. With “you build it, ops sometimes run it,” some services are run by the development teams and others are run by the operations teams. The decision for which services should be run by which team can be based on the service availability target.

- Services with high availability targets need to be run by the development teams due to high business demand and the need to recover from incidents quickly. 
- Services with low availability targets can be run by the operations teams because they have lower business demand, and therefore a longer time to recover from incidents might be acceptable.

The “you build it, you run it but some specific use cases are additionally monitored by ops” model refers to the development teams generally running their services in production.

Because the teams run their services themselves, they may already be aware of the issues and are working on them. The value of the additional monitoring by ops is in the additional ability to detect cross-team issues that inhibit execution of the most frequently used or most critical workflows in the system.

#### 12.2.3 Reliability Incentives 
With “you build, you run it,” the development teams have the most incentive to implement reliability into their services. This is because they are the ones who bear the full brunt of the 24/7 on-call rotation.

The incentives may diminish slightly with the “you build it, you and SRE run it” shared on-call model.

Only part of the 24/7 on-call responsibility is borne by the development teams. Another diminishment of incentives takes place with the “you build it, SRE run it” model.

- A downright drop in incentives for the development teams to implement reliability takes place with the “you build it, ops run it” model.

- Issues with the "You Build It, Ops Run It" Model

| Issue | Explanation |
|----|----|
| Long incident resolution times | The operations teams possess limited knowledge about services in production. Therefore, they cannot resolve lots of incidents directly. Rather, the development teams need to be consulted. First, it takes time to get the incidents to the development teams. Second, it takes time to get the incidents prioritized by the development teams.
The development teams are never on call. Therefore, work on the incidents almost never starts immediately once an incident occurs. All this adds up to long incident resolution times. |
| Large number of workarounds | It takes a long time for the development teams to resolve an incident. However, customers often cannot wait that long. Therefore, the operations teams create workarounds in production to get the services working on a temporary basis. Once the development teams fix the issues, the fixes might interfere with the existing workarounds during or after the deployment. |
| Lack of knowledge synchronization | The knowledge gap between the development and operations teams is very large. They literally live in two different worlds. To bridge the two worlds, extensive knowledge synchronization is required. In practice, this is rarely achieved. | 
| Limited adaptive capacity in the architecture | The services are architected with insufficient adaptive capacity. Therefore, they are not resilient to failure in production. A failure easily becomes cascading. The failure blast radius is not limited by technical means, such as stability patterns. |
| Limited adaptive capacity in the architecture | The services are architected with insufficient adaptive capaciyt. Therefore, they are not resilient to failure in production. A failure easily becoms cascading. The failure blast radius is not limited by technical means, such as stability patterns. | 
| Limited telemetry | The logging is insufficient for fast investigatinos of product failures in produciton because it is implemented by the develops who never go on call. Based on the insufficient logging and available black box resource consumption metrics, the operations teams can build dashboards and implemenet alerts that can only superficially relect the state of services under operation. |
| Limited understanding of infrastructure and service interplay | Because the operations teams possess limited knowledge about the services in production, their understanding of the interplay between the services and the underlying infrastructure is also limited. The interplay requires special knowledge of deployment, traffic, security, authenticaion, and authorization infrastructure. That knowledge is typically not available with the operations teams in the depth necessary for effective and fast incident resolution. |
| Collaboration issues during incident response | The development and operations teams generally have different ways of working. Moreover, the development teams do not have access to produciton. The operations teams do. Therefore, in all likelihood the operations teams will have a different set of tools than the development teams. These factores will lead to collaboration issues between the development and operations teams during incident reponse. |

#### 12.2.4 Model Comparision Criteria
When comparing “who builds it, who runs it?” models, many criteria can be taken into account. The criteria need to be selected in such a way that they help a product delivery organization choose a suitable model. The following set of comparison criteria is exemplary but representative:

- Invovlement of the development teams in the on-call work
- Knowledge synchronization between teams
- Incidnet resolution times 
- Service handover for operations 
- Establishment of a distinct SRE organization
- Ownership of the SRE infrastructure 
- Availability targets and product demand
- Funding
- Cost

#### 12.2.5 Model Comparision
- Comparision of Models from the "Who Builds It, Who Runs It?" Spectrum
| Criterion | You Build It, You Run It | You Build It, You and SRE Run It | You Build It, SRE Run It | You Build It, Ops Run It |
|----|----|----|----|----|
| Involvement of the development teams in the on-call work | Max | Continuous | None if services within error budgets | None |
| Knowledge synchronization between teams | None | Partially required | Required | Not practical |
| Incident resolution times | Min | Short | Short | Max |
| Service handover for operations | Not applicable | Partically required | Required | Required |
| Establishment of a distinct SRE Organization | Not applicable | May be an option | May be an option | Not applicable |
| Ownership of the SRE Infrastructure | Ops org | Either SRE or ops org | Either SARE or ops org | Ops org |
| Availability targets and product demand | Highest targets and demand | Highest targets and demand | Highest targets and demand | Lower targets and demand |
| Funding | CAPEX | CAPEX | CAPEX | CAPEX |
| Cost | High | High | High | Low |

In summary, it can be said that the “you build it, ops run it” model bears lower cost but does not exhibit characteristics necessary for operating the services reliably at scale. The other three models—“you build it, you run it,” “you build it, you and SRE run it,” and “you build it, SRE run it”—bear higher cost but are suitable for ensuring reliable service operations at scale. These three models represent quite comparable alternatives.

### 12.3 You Build It, You Run It
The organization is responsible for building and running services. This can be done in slightly different ways team by team. In the development organization, three development teams are shown. These teams fulfill the SRE responsibilities slightly differently.

Development team 1 does not have a dedicated SRE role. Rather, the responsibilities for running services are borne by the entire team, with developers working on certain SRE aspects on rotation. For example, the developers may go on call on a rotation basis. A distinct characteristic of the team 1 setup is that there is no dedicated SRE role or person in the team.

Development team 2 is organized differently. There is a dedicated SRE role in the team, and the role is assumed by a dedicated person. The developers on the team build the product and the SREs run it. Team-internal knowledge sharing procedures ensure the development knowledge flows from developers to SREs and vice versa.

That is, the distinct characteristic of team 2 is that there is a dedicated SRE as part of the development team. The SRE takes part in all the team activities: daily standups, backlog grooming, demos, retrospectives, concept discussions, and so on. Therefore, knowledge between the SRE and the developers flows naturally for the most part, with ongoing team rituals and activities.

> <b>Key Insight:</b> If there is a dedicated team-internal SRE as part of the development team to run the services owned by the team in the "you build it, you run it" model, knowledge betweeen the SRE and the dev elopers flows naturally for the most part, with ongoing team rituals and activities. The SRE is a full member of the development team and takes part in all the team rituals and actvities like every other team member. 

Development team 3 is organized as a combination of how development teams 1 and 2 work. Team 3 has a dedicated SRE running the services. Additionally, the developers join the SRE to run the services on rotation. Operational knowledge between the SRE and the developer flows naturally as part of shared on-call work when they run the services together.

It is important to note that in the “you build it, you run it” model, the different setups to run the services in a team can be decided flexibly team by team. What is more, a team can change the setup over time to suit their unique circumstances. For example, a team might start without a dedicated SRE, with the operations work done by the developers on rotation. At some point, the team might decide to add a dedicated SRE to better cope with the operations work due to the rising popularity of the service. Later, when the SRE leaves the organization to pursue other opportunities elsewhere, the team may switch back to running the service without a dedicated SRE. At some point in the future, when a new SRE has joined the team, they might organize a shared on call with the SRE and one of the developers on rotation running the service.

- The flexibility is there. The decisions can be made quickly by the team.

- “You build it, you run it” is a very scalable model. It scales easily as the number of development teams in the development organization grows.

- Ways of Running the "You Build It, You Run It" Model 

|  | You Build It, You Run It | You Build It, You Run It | You Build It, You Run It | 
|----|----|----|----|
| Who Operates Services Within the Development Team? | Developers operate the services | SRE Operates the services | SRE and developers operate the services |
| Are SREs full Development Team Members? | N/A | Yes | Yes |
| What Is The Reporting Line of SREs? | N/A | Development manager -> Head of Development | Developement manager -> Head of Development |
| What Are The Incentives of SREs? | N/A | Incentives are aligned with the development team goals | Incentives are aligned with the development team goals |
| What Is the Scalability | Scale the number of development teams | Scale the number of development teams. Each team gets a dedicated SRE | Scale the number of development teams. Each team gets a dedicated SRE |

### 12.4 You Build It, You and SRE Run It

