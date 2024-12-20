+++
date = '2023-06-08'
title = 'Kubernetes vs. Serverless:'
+++
### Kubernetes vs. Serverless: Which Is Best For Your Applications?

Microservice development has been around for some time and only continues to improve in popularity due to its flexibility and natural ability to accommodate scale.

Containers are a great way to run microservices and Kubernetes (often abbreviated as k8s) and Docker are the clear favorites. Developers build their containers in Docker on the laptop and DevOps deploys the same to the k8s cluster in the cloud.

But there are growing questions around Serverless functions like Lambda and Azure Functions. They feel like they can do the same thing as containers, but with less overhead.
### What are orchestrated containers?

Kubernetes is the most popular method of coordinating multiple containers in a server environment. Generally, this activity is referred to as “Container Orchestration,” and includes Kubernetes, Elastic Container Service, Docker Swarm, Hashicorp Nomad, and managed Kubernetes services like Amazon EKS and Azure AKS.
### Choosing Between Containerized & Serverless

At AIM Consulting, we have built dozens of software systems in high-performance, high-complexity, mission-critical applications.

Our clients are Fortune 200 companies doing millions of dollars of business every day, mid-size companies looking to compete and grow, and startups racing to get their ideas into the marketplace ahead of the competition. We build multi-tier web applications, internet-facing APIs, and system integrations in Java, C#, Python, and JavaScript across the major cloud providers.

When developing these applications, teams must choose between the use of orchestrated containers or serverless functions in order to write their logic. Both have advantages and robust communities around them.

#### Things to know about Serverless vs. Containerized for High-Value Applications:

* Architectural Advantages
* Coding Style
* Platform Knowledge
* Data and State
* Environment Management
* Operational Support

### Architectural Advantages of Orchestrated Containers vs. Serverless Functions

Many articles have been written about the architectural advantages of both serverless functions and orchestrated containers. Some of the topics these articles cover are:
Orchestrated Containers | (k8s)	Serverless Functions
------ | ------
Better for consistent loads	| Better for variable loads
More control	|Never think about servers
Any language you choose	| Natively supports many languages
State can be kept |	Inherently stateless
Require a host |	Near zero cost to start

The operation of these technologies is a significant factor in choosing your architecture, but developer experience is equally important and can seriously impact the long-term success of a project.

Serverless functions and orchestrated containers are both excellent fits for microservice applications, but the planning and development experiences differ greatly. Both are designed to react to load, and both require an understanding of their service platform.

The differences start to emerge when looking at the activities of software development and the structure of the code.
### Coding Style: Orchestrated Containers vs. Serverless Functions
#### Containers

Containers are essentially standalone bundles that provide a runtime ready for execution. They abstract the environment away from the operating system so the bundle can be run with familiar runtimes like Flask, ASP.NET, and Spring Boot.

Once you decide the scope of a microservice, developing the code mirrors development on a bare-metal operating system. The migration from development system to datacenter is straightforward and less traumatic.
#### Serverless

Serverless is just that, serverless; no Tomcat, no ASP, no Node. The code exists as a function adrift in the universe of the cloud provider. No need to worry about hardware, OS patching, or hardware failure; you don’t get control of any of that. Zero overhead lets developers focus on development.

Simple applications can be incredibly compact – as little as a few dozen lines of code. This makes serverless incredibly powerful, but this elegant new world is very different to create in.

State has to be maintained outside the function using other cloud services, and data relies on cloud storage. The ability to handle massive scale comes nearly effortlessly, but developing for the serverless environment is a considerable shift in mindset.
### Platform Knowledge: Orchestrated Containers vs. Serverless Functions
#### Containers

Plan to spend a good deal of time understanding the quirks of your orchestration platform. Kubernetes is well known to be a field of study unto itself, and containers, sidecars, pods, and cluster networking all have to be understood to be used effectively.

You are also responsible for the management of the operating system of your host machines and deciding how much compute resources to dedicate to the cluster to handle load.

There are great tools and knowledge to manage all of these elements, but those do not free you from having to make those decisions and understand the platform.
#### Serverless

You live in your cloud, and your cloud platform is the thing that invokes your code. There is no webserver, but you configure an API gateway, there is no file system, but you save to a database or mass storage.

A solid understanding of your cloud provider’s services is essential, and that knowledge is only minimally transferrable to other clouds. Massively capable applications can be built by connecting services together with very little code, but the nuance of those services can be hard to grasp at first.
### Data and State: Orchestrated Containers vs. Serverless Functions
#### Containers

You really should write your services to be completely stateless, but you don’t actually have to. You have a hard drive and shared memory at your disposal, and it is feasible to maintain state between processes.

State across a container introduces the risk of really gnarly bugs in race conditions and concurrency and reduces the determinism of how requests are handled. Although total zen-like statelessness is not required, it is strongly desired.

This ability makes it possible to lift older processes with shared state possible, but plan to get out of that soon. Do all of your i/o to shared storage and databases.
#### Serverless

As serverless is native to the cloud, reading and writing to the cloud services that complement it is more natural and simpler. Processes are ephemeral, and it is near impossible for stateful things to happen.

This encourages good habits for strict inputs and outputs and even makes separation of concerns more natural.

Cloud providers do allow process orchestration to take place in things like AWS Step Functions and Azure durable functions, which manage state, but those are not to be confused with services like Lambda and Function Apps.
### Environment Management: Orchestrated Containers vs. Serverless Functions
#### Containers

Managing graduated environments is an essential part of professional software development and container orchestration systems are particularly adept at having naturally separated sandbox, dev, test, UAT, staging, and any other number of environments.

An orchestration cluster operates across multiple computers and can manage a highly flexible number of containers. This makes it simple to build and have a different cluster for each named environment. The separation between the groups is natural and offers a low risk of messages leaking from one environment to another.

Deployments using Helm, Kubectl, or other control tools are well understood and can update software seamlessly with zero downtime.
#### Serverless

Environment management is less natural in serverless systems. Every serverless process has a universally unique name and when one service talks to another it needs to know that name. API gateways and DNS can help with this but those are more services to manage and can increase overall complexity when attempting to reduce the logical complexity of the system.

DevOps tools like Terraform, serverless.com, AWS CDK, and Azure Bicep have ways of arranging environments using the concept of ‘stacks’ but this requires an understanding of these tools and the correct use of them.

Overall, there are lots of good ways to create separation between environments. But the technology itself is not opinionated on how to do it, and in many cases, you must be responsible for managing the risk of cross-contamination yourself.
### Operational Support: Orchestrated Containers vs. Serverless Functions
#### Containers

Kubernetes and its contemporaries are complex systems that require a platform operations team to manage clusters. It is possible to partially get these services with managed Kubernetes services from your cloud provider, but somebody has got to do it.

Containers are best run in integration with a container registry used to store and version container images, and that is one more thing to manage beyond your application code. But debugging containers can be done directly in familiar tools to manage processes, memory, and storage like you do on native hardware.
#### Serverless

While you will have a lot less stuff to manage with serverless, being able to tell what is happening in your processes is a very different experience.

Logging and tracing are more important than ever and require that you use your cloud’s native logging tools like CloudWatch or application insights. Debugging is then done through reading logs.
#### So Which is Best: Orchestrated Containers or Serverless Functions?

Both container orchestration and serverless functions are extremely flexible and powerful tools to build modern applications on top of.

Containers are more like working with VMs or bare metal operating systems and so are more familiar to developers and a more natural fit for incremental improvements in legacy systems.

Serverless functions are more lightweight and more flexible, but this requires developers to think about cloud and service layouts first rather than getting in and coding on day one. This is less natural for many teams and may require a steeper learning curve. But teams that want to invest in ways to move fast and build for the future will benefit greatly.

*This article was written as part of work I do at AIM Consulting, part of the Addison Group. Its original article can be found at [https://aimconsulting.com/insights/containers-kubernetes-vs-serverless-functions-application-development/](https://aimconsulting.com/insights/containers-kubernetes-vs-serverless-functions-application-development/)*
