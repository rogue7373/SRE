# Chapter 9 - Implementing Incident Response
By now the teams have defined SLOs in an iterative manner, implemented on-call rotations to react to SLO breaches, and set up stakeholder notifications to keep stakeholders abreast of major outages. With that, the basics of an incident response process are laid down in the product delivery organization: Inci- dents are being detected and worked on by the teams, and the stakeholders are being informed about major outages before customers complain. 

The next evolutionary step in the incident reponse process is to define an incident classification scheme and set up appropriate responses based on incident class. 

### 9.1 Incident Repsonse Foundations
An incident is defined as: An event that could lead to loss of, or disruption to, an organization's operations, services, or functions.

ITIL specifies a detailed incident response process that has five steps. 
1. Incident identification
2. Incident logging
3. Incident categorization
4. Incident prioritization
5. Incident response 
    - Initial diagnosis
    - Incident escalation
    - Investigation and diagnosis
    - Resolution and recovery
    - Incident closure 

With the SRE methodology in place, the preceding steps are covered to some degree. The goal of defining an incident response process is to strengthen the points where necessary to achieve a robust and repeatable process for handling incidents. The process needs to be defendable in audits of various kinds. This generally means it needs to be written down and adhered to. Further, the evidence of process adherence needs to be produced on request.

### 9.2 Incident Priorities
So far, the SLOs and, consequently, the SLO breaches were not assigned explicit priorities. This does not mean the teams did not prioritize them internally. They probably did, in order to know which SLO breaches are more important than others and to act accordingly. To strengthen the incident response process, more consistent, explicit, and transparent SLO prioritization needs to take place.

- SRE coaches need to initiate a generic definition of incident priorities for the product delivery organization. 
- Teams will use the generically defined incident priorities to categorize their SLOs accordingly within the unique contexst of their domain. 
- This will result in cross-domain standardization of incident priorities used by all the teams in the organization. 
- Alignement on incident priority, this standardization allows for everyone to be able to speak to the priority in the same manner, regardless of the domain they support. 

> See figure 9.1 Organization-wide incident priorities versus team-local SLOs

> See figure 9.2 Mapping team-local SLOs to the organization-wide incident priorities

In terms of tool support, setting incident priorities is supported by all common on-call management tools available on the market. 

#### 9.2.1 SLO Breaches Versus Incidents 
