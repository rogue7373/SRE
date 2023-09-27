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



> Key Insight: The art of SRE transformation is to find the degree to which developers need to go on call for their services to maximize learnings and incentives so that they take into account operational concerns during service development. This is going to be different for each organization.
