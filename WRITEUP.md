
| | VM  |  App service|
| - | - | - |
| Type of resource| **Infrastructure as a service**: more things to manage, install and take care of. |  **Platform as a service**: Another level of abstraction for a better user experience.|
| Costs per month | For a Basic tier 2 GB RAM, 1 core, 10 GB storage 500 MXN | 1.75 GB RAM, 1 core, 10 GB storage 1000 MXN, this is more expensive, you have to do less work, it makes sense|
| Scalability | Yes | Yes |
| Workflow | More work on your side, not necesarilly harder, but it will certainly take more time, steps or maintenance. | Easier, specialized |
| Availability| Traffic manager by azure | Traffic manager by azure |

If the priority for you as a developer is to have the web app running, an app service is the best solution because you don't need to worry about the environment that it's running on. This is my case. I have a web app that I can edit and develop, on each commit it can be deployed with azure pipelines, and I don't need more control of the backend than what I already have.

---
### Assess app changes that would change your decision.

*Detail how the app and any other needs would have to change for you to change your decision in the last section.*

The app service is tied down to a python web app from the moment I create it. If I knew I'm starting with python but changing frameworks soon, it would be better to use a VM.

If I needed to configure more things on the web server, maybe the VM is not the only other choice. I could use a container solution, where the web server is a separate service from the web app itself.

A VM offers more flexibility, but allows for bad practices. If a microservice architecture is in place, there are other azure solutions that will keep you in li ne with best practices and give you the reliability you need.

A VM could be a good option for quick prototyping of a messy architecture of multiple services, but I'd be inclined to quickly migrate to dedicated services, or invest the time to learn what is needed to use them from the beginning.

---
### References
https://docs.microsoft.com/en-us/azure/architecture/guide/technology-choices/compute-decision-tree