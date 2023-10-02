# Chapter 9 - Implementing Incident Response
Numerous books and publications recognize culture as a very important factor influencing all aspects of an organization. Both SRE and SRE transformation are among those aspects that are greatly influenced by organizational culture. The speed with which SRE will be allowed to spread will not be determined by the project plans, executive wishes, or SRE coaches’ hopes. Rather, it will be determined by the organizational culture to a great extent.

According to the Longman Dictionary, one definition of culture is: “the beliefs, way of life, art, and customs that are shared and accepted by people in a particular society.”4 Sociologist Ron Westrum defined a popular topology of organizational cultures, often referred to as the Westrum model,5 which classifies cultures as pathological, bureaucratic, or generative according to how organizations process information: Pathological cultures are power oriented, bureau- cratic cultures are rule oriented, and generative cultures are performance oriented. According to DevOps Research and Assessment (DORA6), performance-oriented generative cultures also lead to high performance in software delivery. According to the Westrum model, there are six aspects of a generative culture:

1. High cooperation
2. Messengers are trained
3. Risks are shared
4. Bridging is encouraged
5. Failure leads to inquiry
6. Novelty is implemented

These aspects relate very directly to SRE. 

#### 4.4.1 Is There High Cooperation

Notorious in the realm of production operations are the walls between product development and product operations. On one side of the wall is product operations, whose goal is to keep production stable. This goal leads them not to want frequent changes in production, because each change may cause instability (or typically does, based on their experience). On the other side of the wall is product development, whose goal is to implement, deploy, and release to production new features requested by product management as quickly as possible. DevOps is trying to break down that wall. So is SRE as an opinionated implementation of DevOps.

1. High Cooperation: The purpose of SRE is to align the software design organization on operational concerns. This can only be done with high cooperations between product development, product operations, and product management. 
2. Messengers are trained: Service owners whose services deplete error budgets permaturely need to be trained to implement reliability measures to keep the error budgets. People on call resolving incidents are supported in running blameless postmortems viewed as reliability learning opportunities for everyone in the organization. 
3. Risks are shared: Product operations, product development, and product management need to agree on the SLIs, SLOs, error budgets, and on-call rotation setup. This way, they share the risks of the joint decisions. 
4. Bridging is encouraged: Service SLOs and error budget depletion rates over time need to be made public to create converstations amond teams, leading to data-driven decisions about reliability concerns of dependent services. Moreover, during the SRE transformation, regular exchanges between teams need to be facilitated; for example, using an SRE community of practive or lunch and learn sessions. 
5. Failure leads to inquiry: Incident resolution needs to be followed by blameless postmortems. 
6. Novelty is implemented: New insights from production operations need to lead to reliability features being implemented in the product in a timely fashion. 

#### 4.4.2 Are Messengers Trained
- Are teams shot down by management for production incidents? 
- Are postmortems held after production incidents? 
- Do people fear being blames in postmortems? 
- Are people who voice reliability concerns neglected? 
- Do production defects lead to scapegoating in the organization
- Does premature error budget depletion lead to reliability training? 
- Are discussions about postmortem summaries viewed as reliability learning opportunities? 

#### 4.4.3 Are Risks Shared
- Are repsonsibilities around production operations clearly written? 
- Are the written responsibilities around production operations known to the operations engineers? To the developers? To the product owners? 
- Do developers share in the risk of production operations? If so, how? 
- Do product owners share in the risk of production operations? If so, how? 
- Do product operations, product development, and product management make join decisions and bear shared consequences for the decisions about SLIs, SLOs, error budget policies, and on-call rotation setup? 

#### 4.4.4 Is Bridging Encouraged
- Are postmortem summaries readily available for reference by anyone in the organization?
- If you picked a developer randomly, would they know where the postmortems are stored? 
- If you picked a product owner randomly, would they know where the postmortems are stored? 
- Are postmortems written from a user impact point of view and in a way that can be understood by nontechnical people in the organization? 
- Is there a regular exchange about the postmortem content with a wider audience? 
- Is anybody reading postmortems and learning from them? 
- Is there a community of practive (CoP) for operations or, more specifically, SRE? 
- Do operations engineers get involved in any product creation activities? 
- Do product operations, product development, and product management have regular exchanges to refine SLIs, SLOs, error budget policies, error budget-based decision-making, and on-call rotation setup? 

#### 4.4.5 Does Failure Lead to Inquiry
- Do hotfixes lead to punishment of teams and individuals by management
- Who initiates a postmortem
- Is there a clear set of criteria that an incident must have in order for a postmortem to be initiated
- Do people feel psychologically safe taking part in a postmortem? How do they know this? 
- Are there action items from postmortems that lead to reconsideration of SLIs, SLOs, and error budget policies? If so, how are the action items followed up on? By whom? 

#### 4.4.6  Is Novelty Implemented
- Do statistics about services depleting their error budgets permaturely lead to scapegoating in the organization? 
- Do statistics about services depleting their error budgets prematurely lead to user story backlog prioritization decisions based on previously agreed error budget policies? 
- Are production releases seen as experimentation opportunities used to test previously defined feature hypotheses? 
- What is the process of learning from one productions relase to inform the development of the next production release? Is it structured? 
- What is the average lead time for a technical novelty identified in a postmortem to be prioritized in the user story backlogs of teams that needt o contribute? 

### 4.5 Where Is the Process
The last dimension to assess in the product delivery organization is the overall process of getting production operations done. The process consists of many subprocesses and involves many teams. The following questions can be helpful in developing an understanding of where the pro- cess and its subprocesses currently are:

Customer Support: 
- How do the customer support requests reach development teams? 
- What is the interface between customer support and the development teams? Tickets? Regular meetings? ChatOps? 

On-call Process: 
- Is there anybody on call for services? 
- What is the availability of the on-call coverage? 24/7? 
- Are there on-call rotations? If there are:
    - Which roles are on the rotations? 
    - How is knowledge handover organized when people switch? 
    - Is there a primary and secondary on-call person per shift? 
    - What is the typical duration of an on-call shift? 
- Are there runbooks? If so, who keeps them up to date? 

Incident Reponse: 
- For incidents involving several teams, are there incident commanders? 
- Who gets assigned which incidents? 
- What is the average incident resolution time? 

Productions access control: 
- Is production access needed for humans? If so:
    - Who can get it? 
    - How do they request it? 
    - How quickly is access provided after a request has been placed? 

Regulatory Compliance: 
- How often must the health of deployed services be checked? 
- What artifacts are required to make a production deployment? 

Production Deployment: 
- Can a team do a production deployment themselves in an autonomous fashion? 
- Do stakeholders or customers need to be informed before a production deployment can be done? 
- Is there downtime during a production deployment? How long is it on average? 
- How often are production deployments done on average? 
- Is there a definition of production deployment failure? 
- How many productions deployments fail on average within a time unit? 
- What is the average productions failure recovery time? 
- Are there manual steps to be done to accomplish a production deployment? 

Production Release: 
- Is a production release to customers decoupled from a production deployment to a data center? If so, who can make the release to customers and on whose behalf? 

Hotfix Deployment: 
- What is the difference in deployment process between a hotfix and feature deployment? 
- Are manual steps necessary to accomplish a hotfix deployment? 

Hotfix Release: 
- What is the difference in release process between a hotfix and feature deployment? 

Prioritization: 
- Is there a structured process in place that goversn prioritization of reliability work versus user-facing features? 

### 4.6 SRE Maturity Model
Based on the aforementioned considerations in assessing a product delivery organization on various aspects related to production operations, it is possible to create a maturity model for SRE. The maturity model can be used by SRE coaches initially to assess where the organization is before the SRE transformation. Later, once the transformation is underway, the SRE coaches might wish to reassess the organization to check whether different areas are progressing, stagnating, or regressing. Twice yearly might be a reasonable basis on which to conduct a reassessment.

General disadvantages of maturity models apply to the SRE maturity model as well. A matu- rity model assumes a linear progression path to a fixed destination of excellence. However, run- ning an SRE transformation will be different for each team due to their unique sociotechnical circumstances. A fixed destination of excellence as the highest level in the SRE maturity model is surely not the top of the mountain. Rather, it is a continuous refinement of SRE processes and practices by each team that drives a good and sustainable SRE execution.

The SRE coaches should store their assessment results for future reference. Once the SRE foundations are established, a reassessment can be done. The results of the reassessment can then be compared to the results of the original assessment to assess the progress of the SRE transformation.

### 4.7 Posing Hypothesis 
Different parties in the organization have different views about production operations. Especially when the product delivery organization is struggling with ongoing outages resulting in high-profile customer escalations, opinions abound about how to improve the situation.

> See Chapter 4 Figure 4.3 for additional tables. 

A hypothesis is posed before the product delivery teams start working on a product capabil- ity. It is done in plain English using a three-term expression, <product capability> / <customer outcome> / <measurable signal>, as follows.

- We believe this <product capability>
- Will result in this <customer outcome> 
- We will know we have succeeded when we see this <measureable signal> 
