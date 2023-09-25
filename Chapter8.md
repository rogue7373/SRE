# Chapter 8 - Implementing Alert Dispatching
Alert dispatching is about the efficiency with which alerts about breaches and outages reach the people who can take real action. 

The Goal of alert dispatching is to precisely target the appropriate recipients and to provide them with all the information they need to take action. It is also about sending as few alerts as possible. Your on-call staff should only receive alerts about SLO breaches that would impact the customer experience.

- “We do not want to alert you about something you would not react to!” should be the man- tra of SRE coaches during the SLO definition process.

- Stakeholders need to be notified only about high-provide outages so that they know they exist and that the operations and development teams are swarming to resolve them. 

The chapter covers two key points about alerting
1. Escaltions within the product delivery organization
2. Stakeholder gouprs and how to set up stakeholder notifications 

### 8.1 Alert Escalation
