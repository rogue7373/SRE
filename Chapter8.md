# Chapter 8 - Implementing Alert Dispatching
Alert dispatching is about the efficiency with which alerts about breaches and outages reach the people who can take real action. 

The Goal of alert dispatching is to precisely target the appropriate recipients and to provide them with all the information they need to take action. It is also about sending as few alerts as possible. Your on-call staff should only receive alerts about SLO breaches that would impact the customer experience.

- “We do not want to alert you about something you would not react to!” should be the man- tra of SRE coaches during the SLO definition process.

- Stakeholders need to be notified only about high-provide outages so that they know they exist and that the operations and development teams are swarming to resolve them. 

The chapter covers two key points about alerting
1. Escaltions within the product delivery organization
2. Stakeholder gouprs and how to set up stakeholder notifications 

### 8.1 Alert Escalation

This subject covers alert propagation from the main on-call to the backup on-call and beyond. 

Modern on-call management tools allow for sophisticated alert propagation. Propagating alerts from one person to another based on a set of rules is referred to as alert escalation. The set of rules is referred to as the escalation policy. An on-call management tool can reassign an alert between the people on call according to a defined escalation policy.

Example escalation policy: 
1. Chain of people to be notified. A person can be expressed as follows: 
- The current person on call in a defined schedule
- Any responder user
- A defined team of people, in which case all members of the team are notified
- A defined group of people across teams, in which case all members of the group are notified
2. Time span between the alert dispatch to a person in the chain and the alert acknowledg- ment by anyone before the alert escalation takes place. When the time span is expired, the alert escalation to the next person in the chain is automatically performed. If the alert gets acknowledged before the time span is expired, the escalation policy stops.
3. Number of repeats for the escalation policy. Once the defined chain of people has been iterated through and the alert is still unacknowledged, the escalation policy can be repeated. On repeat, the first person in the chain is notified first, the second one second, and so on.

* Refer to Chapter 8, Figure 8.2 for a escalation policy table. 

### 8.2 Defining an Alert Escalation Policy

An alert escalation policy needs to be defined for each on-call rotation. The escalation policy is the manifestation of the on-call setup agreement between the operations engineers, developers, and product owner in the on-call management tool. Following this, the escalation policy and the schedules the policy is based upon may contain operations engineers, developers, or a mix thereof.

> main on-call schedule → backup on-call schedule → repeat once

The alert acknowledgment expiry times for the main and backup on-call people need to be experimented with. The expiry times can vary greatly, ranging from minutes to hours, based on the organization and the criticality of the product.

* Work with the simplest escalation policy for a short while and report positive feedback about it. 

The goal is to fine-tune the escalation policy so that the majority of alerts are acknowledged by the people on call within the defined time spans. In addition, the goal is to have a safety net of the people off call included in the escalation policy to ensure reaction to alerts even if the people on call are unexpectedly unavailable.

> From the Trenches: Start with the simplest escalation policy along the lines of “main on-call schedule → backup on-call schedule → repeat once”. Experiment with the acknowledgment expiry times for the main and backup on calls. After it is calibrated, think about extending the escalation policy beyond the people on call. Tread care- fully to avoid alert fatigue, and iterate based on feedback. Consider the organization’s culture when deciding whether to include managers and executives in the escalation policy.

### 8.3 Defining Stakeholder Groups

Stakeholder notifications can be trig- gered either manually by the people on call or automatically when certain conditions apply. For the stakeholder notifications to be targeted well, two points matter.
1. Stakeholder groups need to be defined with targeting in mind.
2. Stakeholders need to be able to subscribe flexibly to the stakeholder groups of interest.


A stakeholder group needs to be defined in such a way that a certain type of notification can inform the group in an effective manner.

* Refer to Chapter 8, Table 8.2 for details on the above 

The SRE coaches should engage product management, marketing, and sales in defining the stakeholder groups. A few representatives from each department would be needed to create an initial set of groups. The way the marketing, sales, and training departments are organized will determine how best to set up the stakeholder groups. The degree of precision needed to enable good notification targeting will also be determined by how the products are marketed and sold.

### 8.4 Triggering Stakeholder Notifications 
Stakeholder notifications can be triggered in a manual, semiautomated, or fully automated manner. 

Once the stakeholder groups are selected for notification in an automated or manual way, the stakeholders subscribed to the groups get notified. Each stakeholder gets the notifications via a medium specified in the on-call management tool. Commonly supported media are email, mobile app push notifications, text messages, and phone calls.

### 8.5 Defining Stakeholder Rings 

In addition to defining stakeholder groups, it may be useful to also define stakeholder rings in order to stagger the broadcast of information about major outages throughout the organization and beyond. 

* A good way to think about stakeholder rings is to look at the enterprise’s organizational chart and determine how the information about major outages should radiate from the people on call to applicable enterprise functions, as well as how it should leave the enterprise and flow to partners and customers.

This is where stakeholder rings come in handy. They provide structure to radiate information about major outages within the enterprise and beyond in an orderly manner. That is, both internal and external escalations can be supported using stake holder rings.

#### Stakeholder Rings (Layers)
1. People On-Call
2. Stakeholder Ring 1 (Product Management)
3. Stakeholder Ring 2 (Leadership of the Product Delivery Organization)
4. Stakeholder Ring 3 (Markting and Sales)
5. Stakeholder Ring 4 (Partners and Customers) - This is the only stakeholder ring that originates outside of the organization. 

Initially the SREs would drive rings 1-3 and the agreements for putting them into action. 

Overall, the prerequisites for enacting stakeholder notifications by stakeholder rings are as follows.
1. The initial set of stakeholder rings is defined.
2. The stakeholder rings are assigned stakeholder groups.
3. The agreements to enact the stakeholder rings are in place between the product delivery organization and other affected enterprise functions. These might be marketing, sales, communications, regulatory, and legal. It is important to note that the agreements within the product delivery organization are necessary but not sufficient for this purpose!
4. The guidance for using the stakeholder rings is created for the people on call.
5. The people on call confirm that the guidance is clear and can be used for sending out stakeholder notifications.

The people on call set up the automated and semiautomated stakeholder notifications, and they send out the manual notifications. The feedback from the stakeholders needs to be fed to the people on call. 

#### Acting on Feedback 
1. Adapting stakeholder rings
2. Adapting assignment of stakeholder groups to the stakeholder rings 
3. Adapting stakeholder groups
4. Adapting assignment of stakeholders to the stakeholder groups 
5. Adapting the stakeholder notifications themselves 

This is the point where the SRE coaches need to start handing over the responsibility for managing the feedback and stakeholder rings to the operations teams. This requires long-term engagement with people way beyond the product delivery organization within the enterprise. Therefore, it is best done by the people with permanent responsibility for the task.

### 8.6 Defining Effective Stakeholder Notifications 

Effective stakeholder notifications have four common characteristics: 
1. Relevance - Effective stakeholder notifications are relevant. This means the dimensions of geography and product landscape are properly taken into account for a particular stakeholder.
2. Timelines - Effective stakeholder notifications are timely. This means the stakeholders are the first to be informed about an issue directly by the stakeholder notification as opposed to indirectly finding out about it later from a customer, partner, executive, or peer. Moreover, the stakeholder notifications arrive in appropriate intervals so that they neither leave the stakeholders wondering what is going on waiting for an update nor overwhelm them with too many updates.
3. Conciseness - Effective stakeholder notifications are concise. This means the notifications contain all the details necessary to fully inform a particular stakeholder about a particular issue, and only those details. In the majority of cases, the information is sufficient so as not to require the stakeholder to reach out to other people for more details.
4. Brackets - Effective stakeholder notifications are sent out in brackets. The first message of the bracket is about the announcement of a major outage. The last message of the bracket is about the announcement of the end of the major outage. Messages between the first and last brackets inform recipients about the progress being made on the way to recovery. Each message before the final message specifies roughly when the next stakeholder notification will be broadcast.

To kick off the process of defining stakeholder notifications for a service, the SRE coaches should start with the service’s operations engineers, developers, and product owner. The start- ing point is to look at the defined SLOs and ask the following questions.
- Which of the defined SLOs, when broken would represent a major service outage
- Which roles would need to know about the outage
- Why would the need the information about the outages 
- What would they do with the information about the outage
- How do you craft a succint message for the people to communicate the information about the outage in a self-contained and actionable way
- Are there other scenarious not covered by SLOs that would represent major service outages

Based on the feedback, the initially defined stakeholder notifications can be adapted and extended. This is a great way to ensure that when the stakeholder notifications start arriving, their relevance, timeliness, conciseness, and brackets will make sense to the recipients. The defined notifications need to be put onto the SRE wiki in a new subsection, “Stakeholder notifi- cations.” The corresponding links need to be distributed to the people on call.

### 8.7 Getting Stakeholders Subscribed

Once the stakeholder groups, stakeholder rings, and stakeholder notifications are defined, set up in the on-call management tool, and reflected in runbooks, the SRE coaches need to engage with the respective recipient roles to explain the setup and associated tools. The central question to explore and get answered for the stakeholders at this point is: How do you subscribe to the stake- holder notifications?

1. For the stakeholder rings within the product delivery organization those subscriptions should live in your on-call system. 
2. The rings residing beyond the product delivery organization but still within the enterprise should be able to use either the on-call management tool, or email/RSS/SMS
3. For those rings that reside outside of the enterprise, site status page, email, sms, rss feed, etc. 

#### 8.7.1 Subsribing Using the On-Call Management Tool 

The SRE coaches should prepare the operations teams to run onboarding sessions for subscrib- ers to stakeholder notifications in the on-call management tool. The onboarding sessions need to be targeted to nontechnical users. For example, onboarding product management leadership will be different from onboarding operations engineers and developers, which was previously done. If possible and practical, the onboarding sessions need to be conducted without using specific SRE or on-call management tool terminology.

#### 8.7.2 Subsribing Using Other Means

For subscribers using a more common means than the on-call management tool, it needs to be checked whether the tool offers the ability to subscribe to stakeholder notifications without hav- ing to create a user account.

An abstraction layer may be needed or an add-on can be used if there is not an option within the on-call system. 

### 8.8 Broadcast Success 

The following questions can guide the SRE coaches in putting together a concise broadcast on the progress of the SRE transformation.

- How was the information about outages distributed within the enterprise and beyond in the past? 
- How is the information about outages distributed within the enterprise and beyond with the new alert dispatching? 
- What are the typical escalation policies for alerts on SLO breaches? 
- What are the defined stakeholder groups? 
- What are the defined stakeholder rings? 
- What is the stakeholder notification escalation logic through the stakeholder rings? 
- How many stakeholders have subscribed to notifications by the stakeholder group? 
- What is the feedback on the stakeholder notifications from the stakeholders? 

Having some of the stakeholders be part of the broadcast and telling a good story about how their work was improved with the introduced stakeholder notifications is a great way to build credibility right into the broadcast.

