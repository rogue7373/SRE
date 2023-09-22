# Establishing SRE Foundations - A Step-By-Step Guide to Introducing Site Reliability Engineering in Software Delivery Organizations

## Chapter 1 - Intoduction to SRE 

- 1.1 Why SRE? 
The way operations has been done wasn't yielding the desired results alone. This gap in expected results compared to actual outcome causes deliberation within an organization to imporve the way the product is being used. SRE is an concreate opinionated implementation of the DevOps philosophy. 
- 1.1.1 ITIL
ITIL describes IT processes, procedures, taks, and checklists. 
1. Focus on value
2. Start where you are
3. Progress iteratively with feedback
4. Collaborate and promoe visibility
5. Think and work holistically
6. Keep it simple and practical
7. Optimize and automate
- 1.1.2 COBIT
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
- 1.1.4 DevOps
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
