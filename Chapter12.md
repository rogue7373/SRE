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

