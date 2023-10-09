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

| Questions | You Build It, You Run It | You Build It, You Run It | You Build It, You Run It | 
|----|----|----|----|
| Who Operates Services Within the Development Team? | Developers operate the services | SRE Operates the services | SRE and developers operate the services |
| Are SREs full Development Team Members? | N/A | Yes | Yes |
| What Is The Reporting Line of SREs? | N/A | Development manager -> Head of Development | Developement manager -> Head of Development |
| What Are The Incentives of SREs? | N/A | Incentives are aligned with the development team goals | Incentives are aligned with the development team goals |
| What Is the Scalability | Scale the number of development teams | Scale the number of development teams. Each team gets a dedicated SRE | Scale the number of development teams. Each team gets a dedicated SRE |

### 12.4 You Build It, You and SRE Run It
There are two distinct characteristics of the “you build it, you and SRE run it” model: the existence of an SRE team and a shared on-call rotation. The SRE team runs a shared on-call rotation for services in production with the developers of the respective development teams. The SRE team itself can organizationally be placed in the development, operations, or a dedicated SRE organization. In this section, these three alternatives are explored.

#### 12.4.1 SRE Team Within the Development Organization 
The SRE team consists of SREs who support individual development teams. One SRE supports development team 1 and another SRE supports development team 2. The support consists of running a shared on-call rotation with the developers from the respective teams.

Development team 1 has a developer on rotation running the services owned by team 1 together with an SRE from the SRE team. Likewise, development team 2 has a developer on rotation running the services owned by team 2 together with another SRE from the SRE team.

The SRE team decides which SRE supports which development team. Furthermore, the SRE team decides on the duration of stay of a particular SRE with a particular development team. Generally, the duration is rather long-term. The SRE learns about the services they support in a long-term engagement with the development team. They support the team in all SRE-related matters. They are, indeed, essential members of the development team’s incident response process.

- Still, the SRE does not become a full member of the development team. They do not take part in all the development team’s ceremonies. 

> <b>Insight:</b>A general agreement between the development teams and the SRE team needs to govern the SRE engagements.

In terms of “you build it, you and SRE run it” model scalability, if the number of SREs in the SRE team is smaller than the number of development teams, some development teams will have to operate according to the “you build it, you run it” model. This poses a question of scaling the “you build it, you and SRE run it” model. In order to scale it, the number of SRE teams needs to be grown in line with growing the number of development teams in the development organization.

- Example of Scaling the Number of SRE Teams 

| Number of Development Teams | Number of SRE Teams |
|----|----|
| 1 | 1 |
| 3 |   |
| 5 |   |
| 7 |   |
| 9 | 2 |
| 11 |   |
| 13 |   |
| 15 |   |
| 17 | 3 |
| 19 |   |
| 21 |   |
| 23 |   |

With the number of SRE teams above two and growing, the development organization needs to start asking questions about its purpose. Is the purpose of the development organization to build and run products? If so, the number of SRE teams can grow within the development organization. Otherwise, the question of the right home for the SRE teams should be discussed. Would it be appropriate to host the SRE teams in the operations organization? Would it be more future-oriented to create a separate SRE organization and host the SRE teams there?

#### 12.4.2 SRE Team Within the Operations Organization
In this setup, development team 1 is supported by one SRE and development team 2 is supported by another SRE. It is important to note that hte support happens in a cross-ogranziational manner. This means that in this setup, the SRE team will have more organizational power to determine which development teams are supported. By the same token, the SRE team will have more organizational power to withdraw support from a development team. 

The support agreement by the SRE team for the development teams will be more formal. THis will be reflected in the developments teams' error budget policies. In fact, the SRE team may want to put in place a new error budget policy or adapt an existing one to capture the SRE support agreement before engaging with a development team. 

#### 12.4.3 SRE Team in a Dedicated SRE Organization
The SRE infrastructuer team builds and runs the SRE infrastructure. The eingeers building the infrastructure are likley to be called SREs as they reside in the SRE organization. The SRE teams also consists of SREs. THe SREs from teh SRe team support the develpment teams from teh development organization. 

Within the SRE organization, rotation between the SRE team and the SRE infrastructure team will be encouraged. THis way, the SREs gain broad and deep knowledge gboth within the SRE infrastructure and outside where it is used by develpment teams from different subdomains. 

The SRE organization becomes a dedicated hub of SRE knowledge where the infrastructure, best practices, knowledge sharing, incident response, and, indeed an SRE culture are bred and cultivated. 

- Services Offered by the SRE Organization

| Service | Explanation |
|----|----|
| SRE advisory | Reliability advice for organizations and teams. Typically, this would be done without formal deliverables. |
| SRE consulting | Concrete reliability consutlign for teams. Typically, some concrete deliverables will be negotiated. |
| Services co-design | Designing services together with a team, with a focus on reliability. |
| SRE Transformation | Providing SRE coaches to run the SRE trnasformation within an organization or a team. |
| Shared on call | Providing SREs to implement the "you build it, you and SRE run it" on-call model in a team | 
| Dedicated on call | Providing SREs to implement full produciton ownership for an organization with strictly defined entry and exit criteria expressed in terms of service reliability. |
| SRE Infrastructure | SRE infrastructure as a service provided for use by other organizations on a subscription basis |

All seven engagement models are possible. The SRE organization is the organizational unit to explore these opportunites. If the services can be offered successfully internally, they might also be offered externally. If successful, the SRE organization will generate its own external revenue and may turn a profit in its own right. THis would represent a classic example of service externalization after honing and proving the capabilities internally. 

#### 12.4.4 Comparison
The three ways of implementing the “you build it, you and SRE run it” model can be summarized and compared.

- Ways of Running the "You Build It, You and SRE Run It" Model
| Criterion | You Build It, You and SRE Run It | You Build It, You and SRE Run It | You Build It, You and SRE Run It |
| SRE Team Placement in the Product Delivery Organization | SRE Team within development organization | SRE team within operations organization | SRE Team in a dedicated SRE Organization |
| SRE Team Reporting Line | Development manager -> Head of Development | Operations manager -> Head of operations | Head of SRE |
| SRE Team Incentives | Aliged with the development organization's goals | Aligned with the operations organization's goals | Aligned with the SRE organization's goals |
| SRE Team Head Count | Part of the development organization's head count | Part of the operations organization's head count | SRE organization's own head count |
| SRE Team Budget | Part of the development organization's budget | Part of the operation's budget | SRE organization's own budget |
| SRE Team Cost Accounting | Cost accounting within the development organizaiton | Cost accounting within the operations organizaiton or cross-organizational cost accounting | Cost accounting within the SRE organization or cross-organizational cost accounting or by service offered |
| SRE Team KPIs | Set by the development organization | Set by the operations organization | Set by the SRE organization |
| Scalability | Scale the number of SRE teams | Scale the number of SRE teams | Scale the number of SRE teams |

The location of the SRE team in the product delivery organization greatly influences the reporting line, team incentives, head count allowance, budget allowance, cost accounting, and team KPIs. The only constant that does not change regardless of SRE team location is the scalability aspect. “You build it, you and SRE run it” requires at least one SRE from the SRE team to be dedicated to a development team. Following this, the number of SRE teams needs to be scaled with the number of development teams supported.

#### 12.4.5 SRE Team Incentives, Identity, and Pride 
In terms of the SRE team incentives being aligned with the goals of the organizaiton the team belongs to, in the develpment organization the SRE team goals will be more product-centric and product-specific. In the operations organization, the goals will be expressed in more operational terms, such as time to recover from incidents. In the SRE organization, the goals will be expressed in SRE terms, such as error budget depletion. 

Every organization has its own vernacular and, indeed, subculture. Putting the SRE team into a particular organization needs to be done with this aspect in mind. The team will have some shared mindset with other teams in the same organization.

What is more, the SRE team identity will be influenced by the organization it is in. In the development organization, the SRE team identity might be related to the products they support. In the operations organization, it might be related to the efficiency of recovery from incidents and the low number of high-profile incidents. In the SRE organization, it might be related to the user experience in terms of reliability provided when the services are within their error budgets.

Based on the team identity influenced by the organization the team is in, team pride will develop. In the development organization, the SRE team might take pride in the reliability of specific products being delivered. That is, given two different development organizaitons with one SRE team in each of them, each SRE team might take pride in the reliability of the specific products delivered by the respective development organization they are in. The SREs on these teams might 

Based on the team identity influenced by the organization the team is in, team pride will develop. In the development organization, the SRE team might take pride in the reliability of specific products being delivered. That is, given two different development organizations with one SRE team in each of them, each SRE team might take pride in the reliability of the specific products delivered by the respective development organization they are in. The SREs on these teams might specifically care a lot about the products themselves and individual features, not only about reliability in general.

In the operations organization, the SRE team might take pride in the very low number of high-profile incidents of the products they support.

- SRE Team Identity and Pride 

| Product | Development | Operations | SRE |
|----|----|----|----|
| SRE TEam Placement in the Product Delivery Organization | SRE team within the development organization | SRE team within the operations organization | SRE Team in a dedicated SRE organization |
| Team Identify and Pride | Might be product-specific | Might be incident-specific | Might be specific to user experience in terms of reliability |

On the whole, people are influenced by their environment to a great extent. This includes the organizational environment of the team the people are in, which may have an impact on people’s behavior, motivation level, mood, communication patterns, and stress levels. All these factors need to be taken into account when making a decision about SRE team placement within the product delivery organization.

#### 12.4.6 SRE Team Head Count and Budget 
In terms of the SRE head count and budget, the big question is where the funding for the SRE team would come from. Generally, it may come from a budget increase for the entire division or the product delivery organization within the division. Alternatively, the funding may come from an optimization of the division’s or product delivery organization’s existing budget.

The business case for investing in the SRE team may be supported by two aspects: insurance and revenue.

1. The investment in the SRE team is revenue insurance for reliability targets. The reliability targets are expressed as SLOs for different SLIs. To defend them, an SRE team needs to be funded. The funding is a premium for insurance that protects the existing company revenue from reliability damage. That is, the insurance covers a revenue impact risk from reliability damage.
2. The investment in the SRE organization is to seize the opportunity to start a new line of business offering new SRE services. These are SRE advisory, consulting, service co-design, transformation, shared on call, dedicated on call, and SRE infrastructure as a service.

It is important to note that the existing budget reallocation at any level in the organization may come at the expense of other running or planned activities. If this is the case, the respective managers might argue about budget and head count. This needs to be anticipated. The SRE coaches should attempt to smooth the waves as much as possible. A solid explanation of what the SRE team is for and a plausible business case might be able to support the rational side of the argument. War stories of past incidents that were not handled well, consequently impacting customers and the company’s reputation, might support the emotional side of the argument.

The title change might lead to higher wage expectations by the operations engineers. However, it will not lead to the operations engineers supporting the development teams adequately in shared on call as part of the “you build it, you and SRE run it” model. Development and debugging skills are essential for an SRE. An operations engineer who was doing manual operations work might not possess these skills. The SRE coaches should watch this space closely and not spare any effort to prevent such a situation from happening.

In “Aim for Operability, not SRE as a Cult,” Steve Smith says: “In 2020, I learned of a sysadmin team that were rebranded as an SRE team, received a small pay increase... and then carried on doing the same sysadmin work.” To counter this state of affairs, an SRE team must be staffed with engineers combining development and operations capabilities. This is the core reason and the justification for SREs commanding higher wages than operations engineers. The SRE methodology can be learned and the experience applying it can be gained. However, it only works effectively on top of sound development and operations capabilities.

- SRE Team Funding Options 

| Criterion | Product | Development | Operations | SRE |
|----|----|----|----|----|
| SRE Team Placement in the Product Delivery Organizaiton | SRE team placement in the product delivery organization | SRE team within development organization | SRE team within operations organization | SRE Team in a dedicated SRE organization |
| SRE Team Head Count and Budget | SRE team head count and budget | Budget increase to fully/partially cover cost or no budget increase for the development organization | Budget increase to fully/partially cover cost or no budget increase for the product delivery organization |

In terms of head count allowance, the head count is generally dictated by the budget. However, there may be cases in which financial controls impose a head count limit in addition to the budget limit. This might be motivated by the organizational KPIs that measure ratios such as revenue versus head count and profit versus head count.

If a head count limit exists for an organization, it may reduce the maneuvering room for hiring people. For instance, an organization might not be able to hire two junior people fresh out of university instead of a senior person, not because doing so would break the budget limit, but rather because it would break the head count limit. Moreover, even if a senior person leaves a team, it might not be possible to replace them with two junior people even if it could be done in a budget-neutral manner.

#### 12.4.7 SRE Team Cost Accounting 
SRE team cost accounting depends on where the team is located within the product delivery organization. If the SRE team is within the development organization, the cost accounting happens with the development organization itself. The development organization has a cost center within the product delivery organization. The SRE team cost is attributed to that cost center like every other team within the development organization.

The development and operations organizations may have agreed to attribute the cost of SREs to the development organization. That is, organizationally the SREs are within the operations organization, and their salaries are paid by the operations organization. However, the time the SREs spend supporting the development teams (nearly all their work time) is charged to the development organization based on a negotiated transfer price. This is paid by the development organization’s cost center to the operations organization’s cost center, which means there is cross-organizational cost accounting within the product delivery organization.

The development organization contains development teams and the operations organization contains the SRE team. The operations organization negotiates a transfer price for SRE support with the development organization. Typically, the price would be a flat hourly rate for an SRE supporting a development team. The rate would be flat regardless of the actual hourly salary of a given SRE. It would cover an average hourly rate of an SRE and possibly some contribution to the SRE infrastructure cost.

Based on the negotiated transfer price, the operations organization charges the development organization for the hours during which the SREs from the SRE team supported the development teams each month. Thus, the development organization’s cost center contains the costs for the development teams and the SRE support. The operations team’s cost center contains the SRE team and SRE infrastructure costs.

Finally, if the SRE team is within a dedicated SRE organization, there are two ways to do cost accounting. First, the SRE team cost may just be accounted for within the SRE organization. Alternatively, the SRE organization may negotiate a transfer price for SRE support with the development organization and charge accordingly on a monthly basis.

Additionally, the SRE organization may offer many services beyond pure on-call support as part of the “you build it, you and SRE run it” model. These services may be priced and accounted for in different ways.

- Price Models for Different SRE Services 

| Service | Possible Price Model Within The Company |
|----|----|
| SRE advisory | Project price |
| SRE Consulting | Project price |
| Services co-design | Transfer price based on negotiated rates |
| SRE Transformation | Project price or transfer price based on negotiated rates |
| Shared on call | Transfer price based on negotiated rates |
| Dedicated on call | Price based on services supported |
| SRE Infrastructure | Software as a service recurring pricing |


#### 12.4.8 SRE Team KPIs
The SRE team KPIs will be influenced greatly depending on the organization the team is in. For the SRE team in the operations organization, the KPIs may be rooted in incidents. For the SRE team in the SRE organization, the KPIs may be rooted in reliability user experience.

- Exampel SRE Team KPIs

| SRE Team Placement in the Product Delivery Organization | SRE Team Within the Developement Organizaiton | SRE Team Within the Operations Organization | SRE Team in a Dedicated SRE Organization |
|----|----|----|----|
| SRE team KPIs | Rooted in products under development | Rooted in incidents | Rooted in reliability user experience |
| Example KPI 1 | 97% of customer complaints about product A are not related to reliability | Mean time between failures (MTBF) less than two weeks | 90% of supported services are within error budget |
| Example KPI 2 | NPS score of at least 75 for product B | Mean time to recovery (MTTR) from an incident is less than a day | 95% of incidents with supported services consume less than 30% of the monthly error budget |
| Example KPI 3 | Reliability engineering implemented in new product C from the ouset | Number of incidents is on a decline quarterly | 95% of customer complaints for supported services are not related to reliability |

The example KPIs for the SRE team within the operations organization are undergoing criticism in the industry. According to Implementing Service Level Objectives,10 counting incidents is not useful because many incidents with a small user experience impact might be less impactful than a single incident with a severe user experience impact. So, having a small number of incidents is not always better than having a large number of incidents!

The example KPIs for the SRE team within the operations organization are undergoing criticism in the industry. According to Implementing Service Level Objectives, counting incidents is not useful because many incidents with a small user experience impact might be less impactful than a single incident with a severe user experience impact. So, having a small number of incidents is not always better than having a large number of incidents!

Classifying the incidents is very difficult because incidents in complex systems are very often unique. There are multiple and different causes for incidents in complex systems each time they fail. The root causes can be technical and people-related. Thus, counting the incidents by classification is difficult too.

Measuring MTTR can hide the user experience in terms of reliability. While MTTR might be short and get shorter over time, the reliability user experience might not improve. This is counterintuitive but can be demonstrated well using an example (based on a similar example provided in Implementing Service Level Objectives). Imagine six incidents occurring in period 1. Each incident is recovered from within 30 minutes. The MTTR for the six incidents in period 1 is 30 minutes. The downtime in period 1 is 6 incidents x 30 minutes = 180 minutes.

Now imagine period 2. In that period, there is only one incident. The incident was recovered from within 120 minutes. The MTTR for period 2 is 120 minutes. The downtime in period 2 is 120 minutes.

- MTTR Versus Reliability User Experience 

| Criterion | MTTR | Downtime | Reliability User Experience |
| Period 1 | 30 minutes | 180 minutes | Worse than in period 2 |
| Period 2 | 120 minutes | 120 minutes | Better than period 1 |

Period 1 has the lowest MTTR but the longest downtime. Period 2 has the highest MTTR but the shortest downtime. Following this, the reliability user experience in period 2 is better than that in period 1.

### 12.5 You Build It, SRE Run It
A distinguishing characteristic of the “you build it, SRE run it” model is the existence of an SRE team that runs services on their own. That is, in this model the SRE team is fully responsible for running services that were developed by the development teams.

With this comes another distinguishing characteristic of the "you build it, you and SRE run it" model. It is an agreement between the SRE team and the development team whose services are run in production about the minimum reliability to be exhibited by the services for the SRE team to run them. With that, the SRE team only runs services of sufficiently high reliability. If the services do no meetin the reliability criteria from teh agreement, they are not taken into operation by the SRE Team. Likewise, if the services stop meeitng the reliability criteria from teh agreement after being taken into operation by the SRE team, the SRE team can return the services to the development team to operate and improve reliability. 

The agreement between the SRE team and the development team hsoudl be based on the error budget policy. It is the right place to specify and sign off on actions to be taken in cases of permature error budget depletions. 

#### 12.5.1 SRE Team Within a Development Organization 
The SRE team only operates services that stay within defined limits of error budget depletion. The limits are laid down in the error budget policies. There is an error budget policy for development team 1. Likewise, there is another error budget policy for development team 2. It contains agreements between the teams about the kinds of error budget depletion that are acceptable for the SRE team to operate the respective services.

If the services are within the error budget depletion limits specified in the error budget policy, the SRE team keeps operating the services. Otherwise, the SRE team hands over the service operation responsibility to the development team. In this case, the service operation model is switched from “you build it, SRE run it” to “you build it, you run it.”

#### 12.5.2 SRE Team Within an Operations Organization
The SRE infrastructure team is responsible for building and running the SRE infrastructure. The SRE team is responsible for running the services developed by the development teams. The error budget policies regulate the relationship between the SRE team and the development teams in terms of error budget depletion. Consistent premature error budget depletion can lead to the SRE team handing over the service operations responsibility to the respective development team until reliability is improved.

#### 12.5.3 SRE Team in a Dedicated SRE Organization
"You build it, SRE run it" can also be implemented in an organizational structure with a didicated SRE organization. 

The SRE organization in the lower part of the figure runs the services and owns the SRE infrastructure. The infrastructure is built and run by the SRE infrastructure team. It is staffed by SREs with infrastructure knowledge.

The actual operation of product services is done by the SRE team. It is staffed by SREs with the knowledge necessary to go on call for the product services developed by the development teams. To keep the knowledge up-to-date, regular cross-team knowledge sharing between the SRE team and development teams is carried out.

The error budget policies are used to regulate the levels of service reliability necessary to be fulfilled by the services to be operated by the SRE team. Otherwise, the SRE team can hand over the service operations responsibility to the respective development team.

### 12.6 Cost Optimization
Further, the comparison showed that “you build it, you run it,” “you build it, you and SRE run it,” and “you build it, SRE run it” are all high-cost models. They score well on important criteria such as involvement of the development teams in the on-call work, knowledge synchronization between teams, incident resolution times, service handover for operations, and availability targets.

The availability targets offer leeway for cost optimization for the high-cost models. In Imple- menting You Build It You Run It at scale, a notion of team on-call rotations versus domain on-call rotations is explored. For services with high availability targets, a team on-call rotation is recommended. Such a rotation can be implemented with the “you build it, you run it” and “you build it, you and SRE run it” models. The cost of a team on-call rotation is high. It is justified by the high availability targets the rotation is tasked to protect.

For services with medium availability targets, a cost optimization is suggested. It is achieved by setting up a domain rotation instead of a team on-call rotation. A domain rotation supports several services from different teams that share a logical knowledge domain. That is, a person on call from a domain rotation needs to react to the SLO breaches of services owned by several teams. That can only work effectively if the person has solid knowledge of services from the domain regardless of the team owning a particular service.

Thus, the cost optimization with the domain on-call rotations comes from putting fewer people on call per set of teams within a domain. It is justified by the medium availability targets the domain on-call rotation is tasked to protect. With lower availability targets, the error budgets are bigger. The bigger the error budgets, the longer the time to recover from incidents that can be had without depleting the error budgets prematurely.This means the people on-call on a domain rotation would generally have a bit more time to recover from incidents than their counterparts on team rotations protecting high availability targets.

The people from the thin layer are tasked with receiving the SLO breaches from all the teams. Once received, the SLO breaches are triaged. Some SLO breaches can be reacted to by the thin layer using runbooks. The remaining breaches, which cannot be reacted to by the thin layer due to lack of knowledge or capacity, are forwarded to the respective team on-call rotations. The team on-call rotations are typically not available 24/7, but rather on an 8/5 (eight-hour week- days) or 8/7 (eight-hour weekdays and weekends) basis.

### 12.7 Team Topologies 
The team topoligies explored in the previous sections can be summarized as an intersection of the models from teh "who builds it, who runs it?" spectrum and the relevant departments within the product delivery organization. 

- Team Topologies 

| Organization | You build it, you run it | You build it, you and SRE run it | You build it, SRE run it |
|----|----|----|----|
| Developement Organization | <ul><li>Option 1: No dedicated SRE role. SRE is a responsibility borne by all developers on rotation.</li><li>Option 2: Dedicated SRE role in the team.</li><li>Option 3: Dedicated SRE role in the team and a dedicated developer on rotation.</li></ul> | Option 1: SRE Team in the development organization. SRE Infrastructure team in the operations organization. No SRE organization | Option 1: SRE Team in the development organization. SRE infrastructure team in the operations organizaiton. No SRE organizations |
| Operations Organization | SRE infrastructure team | Option 2: SRE Team and SRE infrastructure team in the operations organization. No SRE organization | Option 2: SRE team and SRE infrastructure team in the operations organization. No SRE organization |
| SRE Organization | N/A | Option 3: SRE Team and SRE infrastructure team in the SRE organization. SRE Tool chain procumrent and administration in the operations organization | Option 3: SRE team and SRE infrastructure team in the SRE organizaiton. SRE tool chain procurement and administration in the operations organization |

#### 12.7.1 Reporting Lines 
Following the team topologies, the reporting lines of the developers, SRE infrastructure engineers, and SREs can be determined. 

- Reporting Lines 

| Organization | You build it, run it | You build it, you and SRE run it | You build it, SRE run it | 
|----|----|----|----|
| Development Organization Reporting line | <ul><li>Developers (Option 1)</li><li>SREs (option 2, 3)</li></ul> | <ul><li>Developers</li><li>SREs (option 1)</li></ul> | 
|Operations Organizaiton Reporting Line | SRE Infrastructure engineers | <ul><li>SREs (option 2)</li><li> SRE infrastructure engineers (option 1, 2)</li></ul> | <ul><li>SREs (option 2)</li><li>SRE infrastructure engineers (option 1, 2)</li></ul> |
| SRE organization Reporting Line | N/A | <ul><li>SREs (option 3)</li><li>SRE infrastructure (option 3)</li></ul> | <ul><li>SREs (option 3)</li><li>SRE infrastructure (option 3)</li></ul> | 

The reporting lines are important, as they determine the organizational goals, incentives, and KPIs for the teams and people. For example, in an organizational setup with no dedicated SREs where developers fulfill the SRE responsibilities on rotation (option 1 in the “you build it, you run it” model), all the people working in a team have the same product goals, incentives, and KPIs. These need to reflect all the product aspects, including reliability. Ensuring product reliability becomes everybody’s goal.

In another organizational setup, inserting a reporting line, or organizational boundary, between the developers and SREs might be done deliberately to incentivize development and SRE teams on different aspects. Development teams can be focused on product functionality, and SRE teams can be focused on product reliability.

In this setup, developers and SREs working together are forced to find a good balance and appropriate activities to satisfy one another’s goals. Depending on the goals, the balance might be beneficial for the overall product or it might not be. The usefulness of the balance will be determined by how well the goals of the development and SRE teams interlock. This, in turn, will be determined by how well the development and SRE organizations work together in the goal-setting process. Moreover, the usefulness of the balance will be determined by how deeply rooted the SRE culture is in the product delivery organization.

#### 12.7.2 SRE Identity Triangle
The question of the SREs’ identity plays a big role. Should the SREs have a more product-centric identity, incident-centric identity, or reliability user experience–centric identity? In combination, the SREs should have identity that encompasses the product, incidents, and reliability user experience.

The focus of SREs within the SRE identity triangle will be influenced by the organization they are in. Let us explore the SRE identity triangle in the context of the development, operations, and SRE organizations.

The focus of the identity is product-centric. The reliability user experience and incidents are also an important part of the identity, but within the scope of the product the SREs are working on. The product itself is very important to SREs here. Within the product, the reliability user experience and incidents are the second most important product aspects. Note that the triangle may turn out to be somewhat different, but the defining characteristic of the product-centric identity is that it has the highest score on the product axis.

#### 12.7.3 Holacracy: No Reporting Lines 
When drawing reporting lines for SREs, a new method of organizing enterprises deserves special attention: holacracy. Wikipedia defines it as follows: “Holacracy is a method of decentralized management and organizational governance, which claims to distribute authority and decision-making through a holarchy of self-organizing teams rather than being vested in a management hierarchy.”

A holacracy enterprise does not have bosses or traditional management levels. Rather, it is managed by agile self-organizing networks. Holacracy.org is a good resource to learn how this could be achieved.

The radical enterprises consist of thousands of micro-enterprises. Each micro-enterprise is fully autonomous, self-organized, self-managed, self-allocating, and self-linking to other micro-enterprises.

A radical enterprise is based on radical collaboration. Radical collaboration is achieved through freely given commitments of intrinsically motivated peers. That is, it is always voluntary. In A Radical Enterprise, four imperatives of radical collaboration:

1. Team autonomy in terms of practice, allocation or role, and schedule 
2. Managerial develution or decentrailization of power in terms of governance, complensation, and so on
3. Deficiency gratification in terms of human deficiency needs such as the need for predictability, choice, equity, and positive self-image, and the need for others to believe in us
4. Candid vulnerability as the opposite of defensive reasoning

Radical enterprises succeed through the fusion of the four imperatives. THat said, at the time of writing, it is unclear how SRE could be introduced in a radical enterprise or holacracy. What can be said with certainty is that it will take a new approach to be explored through experimentation. 

Because no industry experience with introducing SRE in a holacracy is known, this topic is not touched upon in subsequent sections. 

### 12.8 Choosing a Model 
The process of choosing a model from the “who builds it, who runs it?” spectrum can be influ- enced by several factors. For one, if SRE is introduced in a greenfield product initiative, there is no existing organizational setup to consider or transit from. 

If, on the other hand, there is an existing organization for operations, it is the transition from the current setup to a new one that is in focus. The model comparison is still useful. However, it only compares the models from the “who builds it, who runs it?” spectrum without considering the transformation aspects and costs of a given transition.

#### 12.8.1 Model Transformation Options 
The current organizational setup for operations may range from unorganized to any of the four models from the “who builds it, who runs it?” spectrum. 

- Model Transition Options Within the "Who Builds It, Who Runs It?" Spectrum

| Transition FROM | Unorganizaed | You build it, Ops runs it | You build it, SRE run it | You build it, you and SRE run it | You built it, you run it | 
|----|----|----|----|----|----|
| Unorganized | - | Possible | Possible | Possible | Possible |
| You build it, ops runs it | No reason | - | Possible | Possible | Possible |
| You build it, SRE run it | No reason | Unlikely | - | Possible | Possible |
| You built it, you and SRE run it | No reason | Unlikely | Possible | - | Possible |
| You built it, you run it | No reason | Unlikley | Possible | Possible | - | 

Moreover, the transition to the “you build it, ops run it” model is unlikely to be done from “you build it, SRE run it,” “you build it, you and SRE run it,” or “you build it, you run it.” 

- Involvement of the development teams in the on-call work 
- Knowledge synchronization between teams 
- Incidnet resolution times 
- Service handover for operations 
- Availability targets 
- Product demand 

All the other transitions in the “you build it, SRE run it,” “you build it, you and SRE run it,” and “you build it, you run it” columns are possible. In fact, the choice between these models could be made on a service basis. It does not necessarily have to be the model for all services in the product delivery organization.

#### 12.8.2 Decision Dimensions 
When choosing a model from the “who builds it, who runs it?” spectrum, one consideration is that the decision is two-dimensional. One dimension is “who runs it?”: “you build it, you run it,” “you build it, you and SRE run it,” “you build it, SRE run it,” or some hybrid thereof. 

Indeed, a service may initially be operated by the development team (“you build it, you run it”). Later, the development team may team up with the SRE team to operate the service jointly using shared on call (“you build it, you and SRE run it”). At some point, the same service may be operated fully by the SRE team supported by the reliability agreement anchored in the error budget policy (“you build it, SRE run it”).

The other dimension of choosing a model from the “who builds it, who runs it?” spectrum is organizational. The decision is weighty. It is made for the entire product delivery organization, and it entails drawing reporting lines for SREs. Therefore, this decision is difficult to change later.

While the “who runs it?” dimension of the decision is important to get right from the beginning, should it turn out to be wrong it can be corrected easily later. The organizational dimension of the decision is more important to get right from the beginning, because should it turn out to be wrong, it cannot be corrected easily later.

- New Director or VP for a New SRE Organization 

| Organization | You build it, you run it | You build it, you and SRE run it | You build it, SRE run it | 
|----|----|----|----|
| Development Organization Reporting Line for SREs | - | - | - |
| Operations Organization Reporting Line for SREs | - | - | - |
| SRE Organization Reporting Line for SREs | - | New director or VP | New director or VP |

With a new director or VP role for SRE created within the product delivery organization, the question is to whom the newly created role should be reporting. Should the new role be reporting to a CTO, CIO, head of the product delivery organization, or head of the product area? What would be the implications of choosing one over the others? Let us consider possible options.

#### 12.8.3 Reporitng Options 
Discussed C-Level leadership in detail, please refer to overly complex, poorly built table that I was not going to spend time trying to put here. Page 436 on the PDF page header, Table 12.19 Reporting Opitons 

#### 12.8.4 Positioning the SRE Organization
Inspired by four types of IT organizations, four types of SRE organizations can be defined in a similar vein: SRE as a cost center, SRE as an asset, SRE as a partner, and SRE as an enabler. 

- Four Types of SRE Organizations

| Criterion | SRE as a Cost Center | SRE as an Asset | SRE as a Partner | SRE as an Enabler |
|----|----|----|----|----|
| Focus on | Cost Reduction | Reliability asset | Reliability business value | Enabling business through reliability |
| Strategy | Reduce cost | Optimize the asset | Exploit revenue | Nurture |

If SRE is viewed as a cost center, the focus will be on reducing the cost incurred by the SRE organization. There might be pressure to cut costs on a yearly basis by innovating within the organization. Other measures, such as cutting the positions once people have left the SRE organization and thus reducing the head count, might be employed as well. In this context, it will be nearly impossible to get an additional budget beyond the initial allocation. This is a difficult position for the SRE director or VP to be in. They should attempt to reposition the organization differently. Any other option - SRE as an asset, partner, or enabler, is a better alternative. 

> If SRE is viewed as an asset, the investments in SRE will be made in pursuit of economies of scale.

This means the SRE infrastructure and SRE coaching will be packaged as products from the beginning. The products will be geared to be sold to different product delivery organizations within the enterprise. The self-service features of the products will be of central importance. This is because these features will drive revenue without adding cost. Self-service onboarding onto the SRE infrastructure, self-service use of the infrastructure features, self-service paved roads for stepwise SRE adoption in teams, and so on will be prioritized. Product management’s goal in this case will be to create infrastructure that is applicable to the bulk of operability use cases that users can fulfill in a self-service manner. Implementing bespoke feature requests to fulfill special corner cases, offering bespoke consulting services, and so on will not be in focus, because they do not contribute to the strategy of asset optimization.

> If SRE is viewed as a partner of business creation, the inception of new revenue streams using SRE will be in focus.

In addition to the generic SRE infrastructure that can be sold as a product, bespoke consultancy services will be on the agenda as well. For instance, SRE advisory, SRE consulting, services co-design, SRE transformation, shared on-call services, and dedicated on- call services will be offered to diversify the SRE revenue streams. That is, the SRE organization will be shaped into a full-fledged business that provides the SRE infrastructure as a core offering and a number of bespoke consultancy services complementing it. It will be an attractive value proposition because it can satisfy nearly any demand for SRE from a single source. The various services on offer can be attractively packaged and rendered in a variety of ways to fit and grow the market.

#### 12.8.5 Conveying the Value to Executives 
The SRE director or VP needs to be aware of the organizational dynamics described in the previ- ous section that arise based on the way SRE is viewed in the product delivery organization. They should work to move the SRE organization toward being viewed as a partner or a business enabler. In order to achieve this, steady engagement with the higher-ups is essential. Depending on the organizational setup, the head of the product delivery organization, head of the product area, CTO, or CIO needs to be engaged. The CEO needs to be engaged as well.

The SRE director or VP needs to be well-prepared for a conversation with a higher-up. They need to have data demonstrating the value delivered through SRE activities. The value can be expressed through the incidents detected and fixed internally before any customer notices the degradation. As demonstrated in “You Build It You Run It,” the value can be demonstrated in financial terms by projecting the ongoing revenue protected. An estimate of the revenue protected through SRE activities is a powerful way to illustrate the SRE value in financial terms that are understandable to C-level executives. The protected revenue can be expressed on a monthly basis or cumulatively by year depending on the level of the conversation.

Further, reputational damage protection is another good aspect to be used in conversations with executives about the value of SRE. It is difficult to express quantitatively, but it can be well-articulated qualitatively.

> <b>Insight:</b> Conveying the value of SRE to executives is best done in financial terms; that is, expressing the amount of ongoing revenue protected and the amount of revenue lost during recovery from customer visible incidents. Investments in SRE can be justified by a growing revenue that needs to be protected and a reduction in the reve- nue projected to be lost during recovery from incidents.

### 12.9 A New Role: SRE 
Depending on the model chosen from the “who builds it, who runs it?” spectrum, a new role for the people practicing SRE may well need to be introduced in the product delivery organization. The need to create the new role needs to be clear and transparent to motivate and catalyze the introduction. Thus, the first question to answer about the new role is why it is needed. This is the subject of the next section.

#### 12.9.1 Why Is a New Role Needed? 
The answer to the question of why a new role is needed can be approached by looking at a general definition of role as a concept. According to Britannica: “A role is a comprehensive pattern of behaviour that is socially recognized, providing a means of identifying and placing an individual in a society.”

Projecting this onto the SRE space, it can be said that an envisioned SRE role is a comprehensive pattern of behavior and reliability practice that is socially recognized in the product delivery organization, providing a means of identifying people who do operations. That is, the roots of the need to introduce a new SRE role lie in the identification and social recognition of the people who do operations according to the SRE principles and practices.

With the “you build it, you run it” model, several options of practicing SRE exist. With option A, the developers practice SRE on rotation. With option B, dedicated people in the development teams practice SRE full time. With option C, the developers practice SRE on rotation and additionally there are dedicated people in the development teams practicing SRE.

> <b>Insight:</b> It is beneficial to introduce the SRE role in any model from the “who builds it, who runs it?” spectrum in order to give SRE activities an umbrella in the organization that can be recognized on par with other activities, such as archi- tecture and development. Moreover, dedicated role definitions and dedicated people assigned to the roles may be required from the regulatory compliance point of view.

The introduction of an SRE role in a conscious manner with a clear definition of responsibilities, skills, and accountability in the context of a given organization has the following benefits:

- Identification and social recognition of people practicing SRE in the product delivery organization
- Recognition of different ways SRE can be practiced: 
    - By Developers on rotation
    - Full-time dedicated SRE practice
    - Full-time dedicated SRE infrastructure implementation and operations 
- Fulfillment of regulatory compliance requirements in terms of roles and responsibilites in operations 
- Enablement of a new SRE career path 

#### 12.9.2 Role Definition 
The graph illustrates very well that SREs need to be involved in all technical phases of the service lifecycle. Additionally, it can be said that SRE involvement is also beneficial before the technical phases begin. That is, when a service is being conceived by the product owners in the ideation and evaluation phases, SRE involvement can provide valuable insights into reliability before decisions are made to further invest in technical implementation.

The design thinking phases can benefit from the involvement of an SRE:

- Empathize → Define → Ideate → Prototype → Test 

Specifically, input into the prototype and test phases can be augmented with reliability thinking in late iterations. The goal of late test iterations is to harden assumptions about the envisioned product being desirable, fulfilling a burning need, and confirming the conditions of product use, user thinking, behavior, and feeling. The hardening can be done in more depth if reliability aspects are explicitly included.

## What Makes an SRE
<b>SRE Responsibilities:</b>

- Maintain system availability 
- Maintain system scalability
- Define and agree on SLIs and SLOs
- Support SLA negotiations 
- Define and agree on error budget policy 
- Make error budget-based decisions
- Set up monitoring 
- Set up alerting
- On call during business hours 
- On call outside of business hours 
- Maintain runbooks
- Take part in postmortems
- Enhance SRE infrastructure 
- Take part in chaos engineering
- Run disaster recovery drills 
- Review service implementations
- Review architectures and designs 
- Improve release procedures
- Support team onboarding onto SRE 
- Participate in SRE CoP
- Contribute to technical road map
- Support first level support 
- Support user testing
- Support requirement engineering 

<b>Skills</b>

- Software engineering
- Software operations 
- Debugging and troubleshooting 
- Distributed Systems 
- Large-scale, high-traffic systems
- Infrastructure as code
- Being driven and self-motivated
- Blameless continuous improvement
- Emotional intelligence
- Ability to perform well on call
- Technical communication
- Stakeholder communication
- Technical documentation
- Ability to work well in short-lived incident response teams

#### 12.9.3 Role Naming
Several role names can be found in the industry describing people practicing SRE to an acceptable extent.

- Current Industry Roles Practicing SRE 

| Role Name | Explanation |
|----|----|
| Site Reliability Engineer (SRE) | The original role name introduced and used by Google. Most commonly used role name for people practicing SRE.|
| DevOps Engineer | A common role name for the people doing operations, implementing deployment infrastructure, and performing deployments. The name originates from the DevOps movement.|
| Produciton Engineer | The role name used at Facebook by the people running the services dedicatedly using the "you build it, you and SRE run it" model.|
| Reliability Engineer | Similar to site reliability engineer (SRE)|
| Cloud site reliability engineer | Same as site reliability engineer (SRE)|

Now, if an SRE transformation has been executed in its pure sense in a given product delivery organization, it should be natural to name the new role “SRE.” However, if the transformation in operations has not been explicitly driven as “an SRE transformation,” there is more freedom to think about role naming.

- SRE Role Names 

| Role Name | Explanation |
|----|----|
| Site reliability infrastructure product owner (SRE Infrastructre PO) | The SRE infrastructure can and should be developed as a full-fledged product using product thinking. To do so, a dedicated product owner is required. |
| Site reliability infrastructure engineer (Infrastructure SRE) | Software engineers implementing the SRE infrastructure used by the development teams can have a dedicated role name. This is justified because the work they do differes from that of an SRE using the infrastructure in a development team. |
| Site reliability platform engineer (Platform SRE) | In a larger product delivery organization, an explicit domain platform may be developed. People working on the domain platform may face unique operational challenges. Therefore, SREs working on the platform development teams may deserve an explicit role name.| 
| Site reliability application engineer (Application SRE) | In a larger product delivery organization, an explicit domain platform may be available that is used by cusotmer-facing applications. People doing SRE on the applicaitons development teams may be given a dedicated role name due to unique SRE challenges with the applicaitons.|

It is worth noting that there are other established role names in operations, such as production support engineer, production systems engineer, technical support engineer, IT administrator, IT support administrator, and IT systems administrator. These roles typically do not practice SRE. Therefore, they should not be taken into consideration when brainstorming potential SRE role names.

#### 12.9.4 Role Assignment 
It is notorious in the industry that if SRE is followed as a cult, occasionally IT administrators might get a different job title and a small pay raise. Otherwise, nothing would change.

To counter this kind of situation, assignment of the SRE role to a person should be done using a properly defined procedure. For existing employees in the product delivery organization transitioning to SRE from another discipline, including IT administration, there needs to be a transition path. These employees need to begin practicing SRE before they are assigned the SRE role. This way, it can be evaluated whether the person can indeed follow the SRE principles and practices. SRE role assignment becomes a culmination in recognition that the person has demonstrated the ability to practice SRE appropriately.

> <b>Insight:</b> This does not mean the person needs to master the SRE practice perfectly and stand the test of time before being assigned the SRE role. 

What it does mean, though, is that the person needs to show aptitude for becoming a good SRE by applying the SRE principles and practices on real products in real life for an appropriately short amount of time.

#### 12.9.5 Role Fulfillment
There are different ways to fulfill the SRE role. They usually fall into three categories: 

1. Dedicated SRE for services (full time)
2. SRE on rotation for services (full time when on call, off-duty when not on call)
3. Dedicated SRE For SRE infrastructure (full time)

- SRE Role Fulfillment Options 

| Organizations | You build it, you run it | You build it, you and SRE run it | You build it, SRE run it |
|----|----|----|----|
| Development Organization Reporting Line for SREs | <ul><li>SRE role on rotation</li><li>Dedicated SRE Role</li><li>SRE role on rotation + Dedicated SRE role</li></ul>| SRE role on rotation + Dedicated SRE role | Dedicated SRE role | 
| Operations Organization Reporting Line for SREs | Dedicated SRE role (SRE infrastructure) | SRE role on rotation + Dedicated SRE Role | Dedicated SRE role|
| SRE Organization Reporitng Line for SREs | - | SRE Role on rotation + Dedicated SRE role | Dedicated SRE role | 

The nature of the SRE role on rotation is that developers perform the SRE activities full time when on call and are off-duty when not on call. Overall, this setup caters to the developers practicing on call in a part-time manner. Interestingly, when developers apply the SRE principles when they are not on call developing code, they implicitly still practice SRE.

The compensation can be monetary, additional time off, or a combination thereof. The following compensation building blocks could be considered:

- Higher base salaries for the people on call outisde of business hours 
- Payment for being on standby outside of business hours 
- Payments for working on incidents outside of business hours 
- Time off following an on-call shift on standby outside of business hours 
- Time off following an on-call shift resolving incidents outside of business hours 
- Payment for keeping the services within error budgets

> <b>Insight:</b> When a product delivery organization is in the process of intro- ducing out-of-hours on call for the first time, there may be a lengthy gray period during which the out-of-hours on-call work is required but not yet properly compensated. While discussions about the compensation are ongoing, the actual out-of-hours on-call work is required to keep the SLAs. In this context, it is common in larger product delivery organizations to find longterm SREs who are willing to be on call outside of business hours without a clearly agreed and enacted compensation model. The managers of the SREs may have legal and other difficulties compensating the effort with monetary payments. However, compensating the effort with additional time off in lieu of additional payments typically can be enabled immediately. Doing so is highly recommended. Leaving the SREs to resolve incidents outside of business hours without any extra compensation will snowball into burnout, resentfulness, and attempts to find another job elsewhere.

### 12.10 SRE Career Path
With the introduction of SRE as a new role in the product delivery organization, an entirely new career path is introduced. The career path needs to be designed as a series of progressive steps. An SRE can take these steps to grow the following aspects of their career:

- Scope of work
- Responsibility 
- Influence 
- Accountability
- Compensation

For additional scope of SRE Career Pathing please see table 12.27 for details broken down by experience 

- Junior SRE 
- Senior SRE
- Principal SRE 

<b>Junior SRE:</b> A junior SRE is responsible for the reliability of services owned by a single development team. They drive the agreements on SLIs, SLOs, and the error budget policy for the team with all the necessary stakeholders. Further, a junior SRE sets up monitoring and alerting and goes on call for the services owned by the team. They implement reliability improvements in the services themselves and the tools in use. A junior SRE is held accountable for the services staying within their SLO and SLA error budgets by error budget period. They are remunerated with a base SRE salary and agreed on-call compensation. To be considered for a junior SRE position, the person needs to have at least one year of relevant work experience. The relevant work experience might be in software engineering, automation, or operations.

<b>Senior SRE:</b> A senior SRE has more responsibility. They are responsible for the reliability of services in an entire domain. A domain typically corresponds to an organizational unit within the product delivery organization. For instance, all the applications implementing food dispatching services in a food delivery organization would represent a food dispatching domain a senior SRE can be responsible for. A senior SRE has all the responsibilities of a junior SRE plus additional work scope. The additional scope consists of driving the SRE community of practice (CoP); reviewing the architecture, design, and implementation of services within the domain; shaping the techni- cal road map; supporting user testing activities from design thinking; and hiring junior SREs.

A senior SRE is held accountable for the services from the domain staying within their SLO and SLA error budgets. To be considered for a senior SRE position at least three years of relevant work experience may be required. The experience should be in a variety of domains, such as software engineering, operations, and SRE.

<b>Principal SRE:</b> A principal SRE is responsible for the reliability of services in an entire business line. A business line is an organizational unit with its own profit and loss (P&L) statement. In other words, it is an own business within an enterprise or the entire business in the case of a smaller company. Like the junior and senior SREs, the principal SRE agrees to SLIs, SLOs, and error budget policies as well as goes on call for some services in the business line. Apart from that, there are distinct new responsibilitiies for the principal SRE.

These responsibilities include negotiating SLAs with customers and partners, driving SRE hiring, and driving new practices such as chaos engineering, disaster recovery drills, and AI ops. Furthermore, a principal SRE is expected to explore new revenue potential with SRE services, such as SRE consulting, advisory, and transformation. These can be offered both internally and externally.
Moreover, the principal SRE is expected to mentor and coach other SREs in the company across all existing product delivery organizations. Mentoring SREs means sharing knowledge and experience. Coaching SREs means guiding them on their way to defined professional goals.

The principal SRE represents reliability as a discipline within and across the business lines. Active participation in relevant internal and external events and conferences and maintain- ing a professional network of peers in different companies is expected from a principal SRE. Leveraging the network of peers, the principal SRE is expected to evolve SRE as a discipline, devising and incubating novel concepts and their implementation.

The principal SRE is held accountable for keeping the SLA error budgets for all services owned by the business line. Moreover, the accountability extends to participation in the SRE consulting and advisory projects that explore new revenue potential. To be considered for a principal SRE position, at least five years of relevant work experience is required. The relevant work experience in this case is in SRE, software engineering, automation, operations, team management, engineering management, technical consulting, advisory, and innovation management.

In terms of remuneration of the on-call duty for all the three SRE roles, an aspect of social justice needs to be taken into account in an appropriate way. For instance, single parents agreeing to be on call outside of business hours may be compensated differently than others. Likewise, people with several children of preschool age might be compensated differently than others.

#### 12.10.2 SRE Role Transitions 
The role progressions should be designed using a set of criteria. As an example, in order to transition from a junior to a senior and from a senior to a principal SRE, the following would need to apply.

- The SRE has performed for more than six months osme of the work usually performed by the SRE role sought to be attained. 
- The SRE has been able to influence pople beyond their current immediate scope of responsibility. 
- The SRE's communication and interpersonal skills allow for connection with a wide range of people and roles on the technical topics presented appropriately case by case. 
- The SRE's work feedback in the last six months by their line manager and others demonstrates potential for assuming more repsonsibility and accountability. 
- The SRE is actively seeking to assume more responsibility and accountability
- In order to attain the principal SRE role: The SRE has served as a mentor to at least one SRE who provided generally positive feedback about the mentorship. 

HR needs to make these transition criteria transparent to the SREs. This way, the SREs have a clear preparation plan to drive their own promotions: The SRE role definitions and the transi- tion criteria between them are clear.

- SRE Head Count by Role 

| # | Junior SRE | Senior SRE | Principal SRE |
|----|----|----|----|
| Number of people | Roughly corresponds to the number of development teams | Roughly corresponds to the number of product domains | Roughly corresponds to the number of product lines |

#### 12.10.3 Cultural Importance 
The SRE coaches should try to sense the level of agreement within the leadership team. In case of a very weak agreement, the SRE coaches should advise the team not to proceed with further communication. Instead, the decision should be brought for further debate until a stronger agreement can be reached.

Once a strong agreement on the chosen organizational SRE setup has been reached in the leadership team, further communication to the current and future line managers of the people practicing SRE should take place. This can be done in a single short meeting. Once the line managers know about the change, the current line managers of the people practicing SRE should let them know about the upcoming organizational change in short, private conversations.

Next, a bigger communication to the people practicing SRE, as well as their current and future line managers, should be made in a dedicated meeting, in the form of a presentation that reveals the business goals supported by SRE, the reasons for the chosen SRE setup in the organization, what it would mean for everyone in the meeting, and how the rollout of the setup is planned to unfold.

The presentation should be held by the head of the product delivery organization or a C-level executive. After the presentation, the presenter, other members of the leadership team, HR, and the SRE coaches should make themselves available to answer questions posed by the audience. People will ask questions regarding their careers, transition plans, remuneration, packages, and so on.

### 12.12 Introducing the Chosen Model
The introduction of the chosen model depends on the changes from the status quo that may have to be done in order to achieve the agreed target state for the product delivery organization. The changes can happen along four dimensions:

1. Changes of the model on the "who builds it, who runs it?" spectrum
2. Organization changes
3. Reporting structure changes 
4. Role changes

The new SRE organization needs to be properly established. To kick off the process, the head of the SRE organization needs to run an all-employee meeting laying down the foundations.

<b>Sample Agenda</b>

- Introduce themselves
- Introducce the vision for the SRE organization
- Introduce the teams within the SRE organization
- Introduce the working mode with other departments
- Introduce the freedom and responsibility split for the teams 
- Introduce the organizational KPIs for the SRE organization
- Introduce the roles in the SRE organization
- Introduce people in the key roles
- Introduce the SRE career path
- Introduce the envisioned head count of the organization
- Introduce the open positions by team
- Encourage everyone to suggest suitable people they know for the open positions
- Introduce the way how the key people can be contacted by anyone
- Introduce standing meetings
    - All-emploee meetings
    - SRE CoP
- Introduce SRE publications
    - blog
    - Availability newsletter
- Introduce immediate new intiatives 
    - Set the purpose
    - Appoint the initiative leader
    - Define success hypotheses
- Talk about the envisioned on-call practice 
- Talk about docking the SRE onto the regulatory compliance
- Introduce the employee performance review process
- Introduce the key supporting people from other departments
    - HR
    - Procurement
    - Workers council
    - Legal
- List open topics
- Open the stage for questions and answer all of the thoroughly

#### 12.12.2 Reporting Structure Changes 
In terms of line management changes, in order to transition an SRE from one manager to another, the recommended approach is to use three meetings:

1. Meeting between the SRE and their current line manager
2. Meeting between the SRE and their current and future line manangers
3. Meeting between the SRE and their new line manager

#### 12.12.3 Role Changes 
Another big area to be taken care of is that of roles and role changes. The introduction of a new SRE career path with dedicated roles such as junior, senior, and principal SREs could coincide with the organization changes for SREs. In this case, the big question when changing the organization is which role will be assigned to a particular person currently practicing SRE without bearing an official role.


##### End of Chapter 

##### Proceed to [Chapter 13](https://github.com/rogue7373/SRE/blob/main/Chapter13.md)


