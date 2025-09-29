# Deep Dive Operational Excellence Pillar

## Operational excellence is the ability to support deveolopment and run workloads effectively, gain insight into operations, and continuously improve supporting processes and procedures to deliver business value. 

## 5 Design Priciples 
1. Perform operation as code - IAC / Lambda
2. small, frequent, reversable changes. Do it often to contindually improve
3. refine operations procedures frequently. Validate that procedures are effective and being used
4. Anticipate failures. Test response failures, frequent test and practice responses
5. Learn from all operational failures. deep dive and learn more. 


## Best Practices
- Organization
- Prepare
- Operate
- Evolve


### Organization
Priorities
- undstand entire workloads and priorities
- External Customer needs, internal costomer needs, governance requirements, compliance requirements, threat landscape, trade offs, manage benefit/risks. 

Models
- Application engineering / Application operations
- Platform engineering / platform operations

Culture
- executive sponsorship, empowered to take action when outcomes are at risk, escalation is encouraged, communications are timely, clear and actionalbel, eperimentation is encouraged, empowered to maintain and grow skill sets, resource team appropriately, diverse opinions encouraged. 



### Prepare
- Implement application telemetry, workload telemetry, user activity telemetry, dependency telemetry, transaction tracability
- Operations - version control, test and validate changes, config management, deployment management system, patch management, design standsards, practices to improve code quality, multiple environments, frequent small reversible changes, fully automate integration and deployment
- Deployment risks - plan for unsuccessful chanbges, test and validate, deployment management systems, limited deployments, parallel environments, frequeent small reversable changes, fully automate integration and testing, automate testing and rollback. 
- Operational readiness and change management - personnel capability, consistent review of readiness, runbooks to perform procedures, playbooks to investigate issues, informed decisions to deploy systems and changes, facilitate support plans for production workload



### Operate
Understand workload health
- KPIs
- Metric workloads
- collect and analyze workload metrics
- workload metrics baselines
- learn expected patterns of activity for workloads
- alert when workload outcomes are risk
- aler when workload anomalies
- validate KPI's and metric effectiveness

Understand operational Health - Basically same as workload
- KPI
- operations metrics
-

Responding to events
- process for events, incident, problem management
- proces per alert
- business impact 
- define escalation paths
- costomer communication plans 
- comunication status through dashboards
- automate responses to events


### Evolve
Learn share & Improve
- process for continuous improvement
- post incident analysis
- feedback loops
- knowledge management
- drivers of improvement
- validate insights
- perform operation metrics review
- document and share lessons learned
- allocate time to make improvements
