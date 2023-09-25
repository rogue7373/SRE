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

