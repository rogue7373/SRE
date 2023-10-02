# Chapter 4 - Assessing the Status Quo
Imagine a product delivery organization similar to the one presented in Section 2.1, Misalignment. In an organization like that, the developers may not understand why they should be doing operations. The operations engineers may not provide frameworks to enable the developers to do operations. The managers may not promote the topic, let alone fund it. What might unite the organization, though, is the desire to finally reduce ongoing high-profile customer escalations of production outages.

### 4.1 Where is the Organization
In terms of the organization, the following aspects need to be considered: 
1. Organizational structure
2. Organizational alignment
3. Formal and informal leadership

#### 4.1.1 Organizational Structure
The first thing to understand about the organization is how product operations are performed based on an organizational chart depicting boxes of departments and teams.
- Which boxes in the organizational chart are formally responsible and accountable for production operations? Is the responsibility clearly depicted in the organizational chart? 
- Does the chart included solid and dotted lines to show who reports to whom in the organization? 
- Is the leadership team aligned with the solid and, if applicable, dotted line reporting? Are there other people on the leadership team? 
- Which boes in the organizational chart are actually keeping the product alive in production? 
- Which boxes are involved in shipping hotfixes? 
- Which boxes are making decisions about prioritization of hotfixes and reliability work? 

What is the status quo? How does the organization cope with production operations at the moment? Given the vision of SRE leading to an aligned organization the organizations path toward SRE transformation might begin to be clear. 

The analysis might reveal that the responsibility for production operations is not clearly defined in the organization. More typically, however, it might reveal that the formal responsibil- ity and accountability of production operations is not well aligned with how the organization is actually coping with the responsibility. Those responsible may not have enough control of the matter to be effective and be held accountable. In a traditional software delivery organization with distinct product development, product operations, and product management departments, the responsibility and accountability of production operations will be with product operations.

#### 4.1.2 Organizational Alignment
Take a look at how the organization is actually getting production operations done today, irrespective of what is prescribed by the formal organizational structure? Production operations might be done in a misaligned fashion with lots of handovers. 

The following questions can guide this analysis: 
- How does customer support work? 
- Who is providing the first level of support in the organization, if any? 
- Who is providing the second level of support in the organization, if any? 
- Who is providing the third level of support in the organization, if any? 
- Are there more than three support levels? How many are there? Who is providing support at each level? 
- What is a typical path for a customer support request through the support levels? 
- What is the trend of customer support request numbers over the last 12 months? 
- What is the average customer support request processing time over the last 12 months? 
- How does the release and rollout process work? 
- How are the decisions to roll out a feature release made and by whom? 
- Is regulatory compliance involved in a hotfix or feature release? 
- Who creates release plans and rollout plans? 
- What kind of coordination is required to do a produciton rollout? 
- Are there release managers to coordinate the production rollout? 
- Is there a team or perosn who typically detects issues in production before the issues make their way throug the customer support levels? 

#### 4.1.3 Formal and Informal Leadership 
Formal leadership is endowed by the organizational structure, informal leadership consists of people who do not wield formal power, but are still great influencers. The benefit of informal leaders is they have to persuade their colleagues using prue logic and emotion. This breeds authenticity. People choose to follow informal leaders, they don't have to. 

- Who is formally in charge of what in the organization
- Who are the informal influencers in the organization? For which areas? 
- Who are recognized experts in the organization? For which areas? 
- Which formal leaders are considered great in the organization? 
- In general, whom do people follow and not follow in the organization? 
- Who are the production heroes involved in all production incidents making the impossible possible? 

Knowing the answers to the above will help garner buy-in for the SRE initiative.

### 4.2 Where Are the People
Exploring the knowledge, mindset, and attitude of people in the organization. 
- This should be explored by role, starting with the operations engineers, developers, and product owners. Architects, managers, and executives are also important to consider. 
- Only a small sample of people should be interviewed to get a feel for where people are on each team. 
- Big / long meetings are discouraged at this stage of the transformation. 

#### Question to Probe With
For operations engineers and operations managers:
- What are your daily tasks?
- What is the general quality of the product?
- How do you decide which alerts to setup?
- Do you know whether these alerts report real issues with the user experience?
- Do you generally go on call? If so, at what times?
- Is there an on-call rotation in your team?
- What do you do if you need a hotfix released and rolled out to production?
- How are developers invovled in production operations? 
- How are product owners involved in production operations? 
- Do you provide a means to enable others to do production operations by themselves? 
- What are teh custoemr support levels in the ogranization? 
- Who is doing which support level in the organization? 
- How are crises in production managed?
- How are customer complaint numbers trending over time?

For developers, architects, and development managers: 
- How do you measure the reliability of the product? 
- How do you decide which reliability features to implement in the product? 
- How do you get the reliability features prioritized? 
- Who prioritizes the reliability features? 
- What happens if a hotfix needs to be rolled out? 
- Does your team do production deployments themselves? 
- Do you ever go on-call? If so, at what times? 
- Is there an on-call rotation in your team? 

For product owners and product managers: 
- What is the vision for your product? 
- Where is the product currently in fulfilling this vision? 
- Who are the users of the product? 
- Who are the customers of the product? 
- What are the most important user journeys for the users and customers? 
- How important is reliability of the product to the users and customers? 
- How are customer complaint numbers trending over time? 
- How do you backlog prioritization? 
- How are reliability features prioritized? 
- Are you involved in production operations? 

For vice presidents and executives:
- What do the customers report about the reliability of the product? 
- How does the organization manage production operations? 
- Is the organization aligned for doing production operations well? 
- Would it be possible to allocate the teams some time for the SRE transformation? 
- Is the funding of the product delivery organization appropriate for achieving the required product reliability? 
- Is there some budget allocated for additional tooling to improve production operations? 

The answers to these questions should provide enough context to understand how people in different roles feel as far as production operations is concerned. This understanding may spark some thinking about the shifts in mindset that would need to take place during the SRE transformation.

### 4.3 Where Is The Tech? 
In terms of the organization's status quo, the next dimension to assess is the technology. 
- Product
- Development
- Capacity Planning
- Testing and Release Procedures
- Postmortem / Root Cause Analysis
- Incident Response 
- Monitoring 

The technical aspects of the hierarchy consist of monitoring, testing and release procedures, capacity planning, and development.

Questions to ask:

Logging and monitoring: 
- Are the services logging? 
- Is the logging done in a uniform way? 
- Is the logging done by all services using the same logging infrastructure?
- Are the services logging into a single instance of the logging infrastructure by production deployment? 
- What instrumentation does the logging infrastructure provide out of the box (e.g, runtime dependency graphs, call durations, etc)? 
- Does the logging infrastructure provide a query language to programmatically query the logs and graph the query results? 
- Is anybody looking at the logs? In which cases? 
- Are there any metrics over the logs? 
- How is logging done for asynchronous operations? 
- How easy is it to analyze asynchronous operations based on the loggs? 
- Is there distributed tracing? 

Testing Questions: 
- Are there tests for services? 
- Which teests are manual? 
- For automated tests, what are the test levels available for services? 
- What is the trigger or cadence of automated test execution by test suite? 
- What is the test execution time by automated test suite? 
- Which test suite gets executed in which deployment environment? 
- Which tests get executed before a feature release? 
- Which tests get executed before a hotfix release// 
- After a deployment is done, are automated deployment checks running to verify the deployment procedure? 
- Are automated teests running in production 24/7? 
- Are the tests and test executions trustworthy? 

Release Questions: 
- Do development teams own deployment pipelines?
- What is the scope of a deployment pipeline? How many services are typically deployed using a single deployment pipeline? 
- Are development teams doing production rollots themselves or are the done by the operations team centrally? 
- What are the manual steps for doing a productions release? 
- Which manual steps ensure regulatory compliance of productions release (docment creation, reviews and signatures, approvals, etc.)?
- How often are prodction releases done on average per team? 
- Is there a canary release process in place?
- How long does it take to roll out a service to all production environments, including a canary release? 
- Are there standard operating procedures (SOPs) describing how standardized work is done in production (e.g., how to manually scale a resource such as memory)?

Capacity Planning Questions:
- Are services running on servers owned by the organization? Are the infrastructure as a service (IaaS) or platform as a service (PaaS)?
- Are several services ruunning in a shared infrastructure unit that can only be scaled by the unit as a whole? 
- Are services running in containers deployed in clusters, such as Kubernetes clusters, so that infrastructure scaling can be done by the container on demand?
- Is infrastructure scaling done manually, automatically, or semiautomatically?

Development Questions: 
- Is the use of HTTP return codes appropriate? For instance, does a "500" error code really mean an internal server error? 
- Does the logging infrastructure provide a log query language? If so, do the developers us the log query language on a regular basis?
- Are services built on the priniciples of the Twelve-Factor App? Are developers aware of them by and large? 
- Do services implement any stability patterns for distributed systems from teh book "Release it! Design and Deploy Production-Ready Software"?

Interestingly, the preceding questions are not closely related to the technology used by the teams. Rather, to analyze the state of tech in the teams from an operational standpoint, more conceptual matters are important. For example, it does not matter which logging infrastructure is used. What is important about it is whether any logging infrastructure is used consistently in the teams so that a single SRE infrastructure can be built on top of the logs benefiting all the teams. Also, if teams do not consistently use a logging infrastructure, they will have before the SRE transformation can progress any further.

The same applies to the release, capacity planning, and development questions. It does not matter which release frameworks are used. What does matter, for example, is whether a canary release is done to test the impact of a change in production on a small group of users first. If this is in place, the team’s release process will be mature. In all likelihood, it will not need to be touched during the SRE transformation.

### 4.4 Where Is The Culture






> Key Insight: The art of SRE transformation is to find the degree to which developers need to go on call for their services to maximize learnings and incentives so that they take into account operational concerns during service development. This is going to be different for each organization.
