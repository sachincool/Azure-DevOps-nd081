
| | VM  |  App service|
| - | - | - |
| Type of resource| **Infrastructure as a service**:  |  **Platform as a service**: |
| Deployment | Self-managed Deployment scripts | Easy out of the box deployment solutions |
| Networking | Need for Custom solutions on top of app for Routing/Networking stack | Built-in A/B testing features|
| Server access  | Full server access to install any agent| No Server access|
|Supported Languages for apps | No-limit  | Limited: ASP .NET, Node.js, Java, PHP, or Python |
| Costs per month | For a Basic tier 2 GB RAM, 1 core, 10 GB storage 500 MXN | 1.75 GB RAM, 1 core, 10 GB storage 1000 MXN, this is more expensive, you have to do less work, it makes sense|


If it's a simple web-app Or a single Service without the complex architecture of microservices. Easy & Fast solution would be web-app.

If the Architecture requires you to monitor custom metrics and Scale on those events, forward logs and create meaningful dashboards, Or use an orchestrator to handle the complex microservices. then VM's will be the go-to solution. you can also Setup VPN's or SIEM solutions to take care of your Architecture.

In my case, It is a simple flask application, with no other dependency on any microservice or app. Hence, I chose web-app for this deployment
---

### Assess app changes that would change your decision

*Detail how the app and any other needs would have to change for you to change your decision in the last section.*

 > These Events Triggers a Shift in the decision: Shifting to microservices, Handling Traffic using a custom/Open-source Load-balancer, Moving Logs from Service to a stdout->Aggregator logging Solution, Any need for a Metrics/Logging agent, Auto-rollbacks of revisions on service failures(I didn't see this in web-app), Cloud-agnostic with a solution like kubernetes (I'm aware we can use AKS for this)

As a first step, I should Package my app as a Docker image, so it can run in any enviroment. I'll need to take care of any Firewall/Networking issues that may arise when I shift (since some rules are Azure agnostic eg: DB Storage firewall)
I'll also need to Create my own solutions for deployments & getting the Logs from VM, and App related metrics which might not be available in VM monitoring

---
### References
https://stackify.com/comparison-azure-app-services-vs-cloud-services/#:~:text=Microsoft%20Azure%20App%20Services%20are,on%20your%20App%20Service%20Plan.&text=Web%20App%20%E2%80%93%20used%20for%20hosting,web%20applications%20(previously%20Azure%20Websites)

https://docs.microsoft.com/en-us/azure/architecture/guide/technology-choices/compute-decision-tree