# On-Call

## Team Based Rotations

Each team has its own on-call rotation, narrowly focused on supporting the specific services you’re actively working on day to day. You’ll be empowered to make changes that improve the performance and availability of those services so that quality metrics can be maintained and improved over time. If you’re on a team responsible for a service that isn’t performing as expected, you’ll be given the time to fix it and make your on-call experience better! This is one of our [engineering core values](values.md) in action.

Each team manages its own rotation and decides on the escalation policy that works for them. Rotations are typically one week long and there may be a primary and secondary, or just a primary with un-ack'd alerts escalating to the whole team. The on-call engineer usually doesn't take on any planned work for the week, so there's never the decision between focusing on an incident versus meeting sprint commitments. He or she can use time not spent on incidents to _sharpen the tools_-improve monitoring, work on automation, or sometimes just to sleep in after a late night page.

## SRE

Fear not, on-call engineer. You are not alone! Our SRE team plays several important roles in the on-call world. In addition to handling many system level alerts (CPU, disk space, borken EC2 nodes, and the like) they also support on-call engineers. During an incident, the SRE on-call will act as the Incident Commander (IC), coordinating the overall response and freeing the engineer to focus on the problem itself. The IC will work with Customer Support (CS) on status page updates and customer communications, pull in other engineers or support staff, and organize the post-incident retrospective.

## Nuts and Bolts

We gather logs into Elasticsearch and [Kibana](https://www.elastic.co/products/kibana). We have graphs and alerts set up in [DataDog](https://www.datadoghq.com/). We use [Blameless](http://www.blameless.io/) to track incidents and support retrospectives. On-call rotations and pages are managed through [Opsgenie](https://www.opsgenie.com/)

Customer impacting incidents are categorized sev0-sev3 based on a number of criteria. Any such incident gets an incident-specific Slack channel created for communication, and _Blameless Bot_ gives us good integration between this and Blamelss itself.
