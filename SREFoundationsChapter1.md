# Establishing SRE Foundations - A Step-By-Step Guide to Introducing Site Reliability Engineering in Software Delivery Organizations

## Chapter 1 - Intoduction to SRE 

### 1.1 Why SRE? 
The way operations has been done wasn't yielding the desired results alone. This gap in expected results compared to actual outcome causes deliberation within an organization to imporve the way the product is being used. SRE is an concreate opinionated implementation of the DevOps philosophy. 
### 1.1.1 ITIL
ITIL describes IT processes, procedures, taks, and checklists. 
1. Focus on value
2. Start where you are
3. Progress iteratively with feedback
4. Collaborate and promoe visibility
5. Think and work holistically
6. Keep it simple and practical
7. Optimize and automate
### 1.1.2 COBIT
COBIT is a framework created by ISACA, it defines a set of eneric processes for the management of IT, with each process defined together with process inputs and outputs, key process-activities, process objectives, performance measures and an elementary maturity model. 

1. Meeting stakeholder needs
2. Covering the enterprise end-to-end
3. Applying a single integrated framework
4. Enabling a holistic approach
5. Separating governance from management 

ISACA released COBIT in 1996. The latest version, COBIT 2019, was released in 2018 and define six governance system principles. 

1. Provide stakeholder value
2. Holistic approach 
3. Dynamic governance system
4. Governance distinct from management
5. Tailored to enterprise needs 
6. End-to-end governance system

Thus, COBIT, like ITIL, is an overarching governance framework for disigning the IT function of an enterprise. 

- 1.1.3 Modeling 
Modeling is applied to find threats. Threat modeling is a risk-based approach for secure system design. It is all about finding security threats based upon analysis of system architecture, implementation, and development. 

Similar to threat modeling in security, modeling as a technique can be applied to find operational vulnerabilities. Your system architecture, implementation, and deployment can be analyzed to find weak spots that would prevent the system from executing well in production.

Modeling requires constant updates to take into account new features, changes in infrastructure, and learnings from productions outages. 
Modeling is not broadly used in the industry. 
### 1.1.4 DevOps
DevOps defines five pillars of success
1. Reduce organizational silos
2. Accept failure as normal 
3. Implement gradual changes
4. Leverage tooling and automation
5. Measure everything 

This is a generic philosophy for bringing development and operations together. DevOps has been widely adopted in the software industry across all domains since 2013. Concrete implementations vary greatly, one of those being the applicaiton of SRE methodolgy. 
The DevOps maturity level of an enterprise can be assessed using the CALMS framework. 
- CALMS: Culture, Automation, Lean, Measurement, and Sharing coined by Jezz Humble. 
- Culture DevOps requires a shared responsibility for tearing down silos between Dev and Ops. 
- Automation in DevOps refers to technical practices around Continuous Delivery (automate all the things, infrasturcture provisioning, deployement, testing, and monitoring)
- Lean refers to the principles of waste elimination and value stream optimization (nod to ITIL)
These methods are applied in practice using work-in-progress minimization, batch size limitation, handoff complexity reduction, queue length management, and wait time reduction
In terms of measurement, a DevOps organization collects data on its processes, builds, deployments, failures, feature usage, etc. This data is used to understand current capabilities and drive measureable improvements. 
- Sharing in DevOps refers to shared goals, openness, and information sharing among the development and operations teams. 
CALMS is also sometimes used to communicate and negotiate the differences between DevOps and ITIL. 
### 1.1.5 SRE 
Site reliability engineering is a probably the latest methodology for doing operations. It originated within Google in 2014. SRE is a discipline that incorporates aspects of software engineering and applies them to infrastructure and operations problems. The main goals are to create a scalable an highly reliable software system. SRE is what happens when a software egineer is tasked with what used to be called operations. 

The SRE principles were postulated by Google in the [Site Reliability Workbook](https://sre.google/sre-book/table-of-contents/) They are described in Table 1.1 in the SRE Foundations Handbook Chapter 1. 

There are also three additional principles for practicing SRE.
1. SRE needs SLO with consequences
2. SREs must have time to make tomorrow better than today
3. SRE teams have the ability to regulate their workload
Thus SRE principles are pretty opinionated and often directly prescribe what needs to be done to achieve reliable operations. 
### 1.1.6 Comparison
Looking at DevOps, SRE, ITIL, and COBIT, a trend emerges dating back to 2014. DevOps and SRE are the operations methodologies with the highest interst. ITIL and COBIT attract the lowest number of searches. 

- ITIL and COBIT are governance frameworks for designing IT function of an enterprise. 
- Modeling is an approach for deriving good operations practices based on an analysis of system artifacts. 
- SRE is rooted in software engineering and approaches operations specifically from that perspective. 
- DevOps is an overarching philosophy for doing operations 

Because the methodologies are so different, they may not be mutally exlusive. They are indeed, addressing different needs. This means that applying of them in combintaion may make sense for a company. 

For example, it may be useful to have ITIL procedures in palce for regulatory compliance handling of customers complaints. While it may also be useful to have SRE in place for proper engagement of developers and operations engineers in operations. As part of SRE activities, some aspects of modeling might aslo be useful while the system is being initially architected. 

While a straight forward comparision of the differences between the methodologies may not be appropriate, it is necessary from an envisioned SRE transformation standpoint. 
- Pointing to SRE because "Google does it" might backfire. This is in part due to the "not-invented-here" syndrome which can often be observed when organizations avoid things created by other organizations. In other words:
- A clear fundamental reason for doing SRE over something else is required. 
It is important to undertake the comparision of the various operational methodologies in order to gain a better understanindg of their posturing in the overall set of operational activites. The suggested following criteria are useful in this decision making:

1. Whether a methodology represents a governance framework to design an enterprise IT function
2. Whether a methodology explicityly supports IT regulatory compliance 
3. Whether a methodology is rooted in IT
* Table 1.2 in Chapter 1 provides a "First Comparison of Operations Methodologies"

With these questions in mind, the next set of criteria can be established to further compare the operations methodologies along the lines of whome in the product delivery organizations they appeal to. 

1. Whether the methodology is appealing to the CIO an operations engineers
2. Whether the methodology is appealing to the CTO and software developers
3. Whether the methodology is appealing to the CPO and product owners
4. Whether a methodology is rooted in software engineering as the core discipline in software product delivery
* See Chapter 1 table 1.3 for additional information

The ITIL framework appeals to CIO's and operations engineers. Being rooted in IT it comes with IT context. Thought not appealing to CTOs and software developers, nor to CPOs and product owners 
* This explains the pushback about ITIL from the above groups and will lower the adoption rate 

When it comes to modeling, ITIL is not appealing to CIOs and operations engineers, because it only addresses part of the IT universe. Modeling is appealing to CTOs and software engineers because it is an analytical appraoch known from the field of security and applied to operations. CPOs and product owners are not going to be attracted to modeling that much as it analyzes technical artifacts like architecture, implementation, and deployment. These artifacts are not where the product people typically have their expertise.

Modeling is not rooted in software engineering, but rather in product security. It represents an established procedure in the product security field, i.e. Threat Modeling. 
The DevOps philosophy is appealing to all groups in product delivery: CIOs with operations engineers, CTOs with software developers, and CPOs with product owners. CPOs with product owners view DevOps as enabling faster software releases and everyone wants faster deployment pipelines. 

CTOs with software developers and CIOs with operations egineers, DevOps is by definition a set of practices that combines development and operations. This is appealing to both groups beecause it attempts to close the chasm between development and operations that is typical in the industry. DevOps is rooted in software egineering. 

Then we have SRE, it will aslo appeal to all groups in product delivery. CIOs and operations engineers will view SRE as an enabler to ensureing that software developers are properly engaged in product operations. SRE operational concerns will be addressed early during the initial product architecture and design phase. Operational concerns will eventually be elevated to the product owners attention. The operational concerns will play a role in product definition and, perhaps most importantly, the capacity distribuition of the development team. 

Additional set of criteria to measure off
1. Whether a methodology aligns the entire product delivery organization, consisting of product managment, product development, and product operations.
2. Whether a methodology is opinionated for operations engineers in that it clearly prescribes what they should do. 
3. Whether a methodologoy is opinionated for software developers in that it clearly prescribes what they should do. 
4. Whether a methodology is opinionated for product owners in that it clearly prescribes what they should do.
* Refer to Chapter 1 - tables 1.4 for additional information

### 1.2 Alignment Using SRE
SRE alignment of the product delivery organization for operational concerns is thus threefold, as shown in Table 1.5
* Chapter 1 - Table 1.5 for reference
1. Joint definition of service objectives
2. Joint definitino of consequences of not meeting the defined service objectives
3. Joint execution on the defined consequences of not meeting the defined service objectives

The value of SRE is bringing the product operations, product development, and product management teams together to ensure proper service operations that lead to a positive customer experience. 

The alignment of the product delivery organization for doing operations suggested by SRE is also required to reach and sustain the speed of DevOps. Consider how difficult it is to gain speed if the product delivery organization is not aligned on operational concerns. If the operations engineers are the only ones ensuring production operations, they will have a difficult time detect- ing issues in production before they are reported by customers. This is because the parameters to alert upon have not been aligned with product development and product management. So, the operations engineers are going to set up alerts on generic IT resources, such as memory con- sumption, CPU usage, queue fill levels, storage consumption, and the like. This kind of alerting, while helpful at times, does not necessarily reflect user happiness while working with the system. So, the user may be unhappy and no alert will be generated. The opposite is also true: The user may be happy and alerts will be generated. This is because the alert definition procedure is not user-centric and does not include all the necessary stakeholders, such as operations engineers, software developers, and product owners.

What is more important: fixing an existing issue in production to make the current users happy, or implementing a new feature to fulfill some existing sales and marketing commitments?

In order to break the tie, the product owner needs to be consulted for a prioritization deci- sion. To make the decision, the product owner needs to understand the production issue first. How many data centers are affected? How many users are affected? Is the issue a blocker for frequently used workflows in the product? Are there any workarounds? What is the impact on revenue? What is the impact on cost? What is the impact on reputation? What is the impact on customer support? How urgent is the fix to be provided? What is the effort to provide the fix? What is the effort to roll it out? What is the effort to monitor the rollout of the fix? These questions are just the beginning of a quest for the right prioritization decision.

* Refer to Figure 1.1 in Chapter 1 to illustrate a siloed vers collaborative work during development and operations. 

This discussion shows that the organization is not aligned on operational concerns. With- out SRE in place, product operations, product development, and product management are not pulling together on operational concerns strongly enough throughout the product life cycle to ensure a positive user experience. What SRE puts in place is an alignment on operational con- cerns among the three parties throughout the product life cycle. This alignment is one of the important enablers of the speed of delivery in the product delivery organization.
SRE is prescriptive about agreements that need to be reached in each stage of the product life cycle. Executing the agreements ensures that product operations, product development, and product management can work in a highly aligned and loosely coupled manner to ensure prod- uct operations in production deliver a positive user experience.

### 1.3 Why Does SRE Work? 
To understand why SRE works, we first need to explore how it works in a more detailed manner than before. The following process is at the core of SRE. 
1. Define so-called service level objectives(SLOs) for services from the user point of view.
2. Measure in production the fulfillment of the SLOs by the service.
3. If SLOs get broken in production, work to bring the services back within the SLOs, or adjust them. 

For example, imagine a service responsible for verifying user credentials. The service exposes some endpoints. The endpoints are used by the service users to get the user credentials verified. The availability of the service endpoints is highly critical. This is because no user can log on to the product if user credentials cannot be verified. Following this, the availability SLO needs to be rather high. For example, it can be set to 99.99% for all endpoints of the user credentials verifi- cation service. This means 99.99% of the calls to the endpoints within a given time frame need to succeed for the service to be within its availability SLO.

