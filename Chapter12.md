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


