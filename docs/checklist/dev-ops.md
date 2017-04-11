# DevOps Checklist

## Culture

**Ensure business alignment across organizations and teams.** 
Conflicts over resources, purpose, goals, and priorities within an organization can be a risk to successful operations. Ensure that the business, development, and operations teams are all aligned, so that a DevOps culture of collaboration and accountability can thrive.

**Ensure the entire teams understands the software lifecycle.** Your team needs to understand the overall lifecycle of the application, and which part of the lifecycle the application is currently in. This helps all team members to know what they should be doing now, and what they should be planning and preparing for in the future.

**Reduce cycle time.** Aim to minimize the time it takes to move from ideas to usable developed software. Limit the size and scope of individual releases to keep the test burden low. Automate the build, test, configuration, and deployment processes whenever possible. Clear any obstacles to communication among developers, and between developers and operations. 

**Review and improve processes.** Your processes and procedures, both automated and manual, are never final. Set up regular reviews of current workflows, procedures, and documentation, with a goal of continual improvement.

**Do proactive planning.** Proactively plan for failure. Have processes in place to quickly identify issues when they occur, escalate to the correct team members to fix, and confirm resolution.

**Learn from failures.** Failures are inevitable, but it's important to learn from failures and avoid repeating them. If an operational failure occurs, triage the issue, document the cause and solution, and share any lessons that were learned. Whenever possible, update your build processes to automatically detect that kind of failure in the future.

**Optimize for speed and collect data.** Every planned improvement is a hypothesis. Work in the smallest increments possible. Treat new ideas as experiments. Instrument the experiments so that you can collect production data to assess their effectiveness. Be prepared to fail fast if the hypothesis is wrong.

**Allow time for learning.** Both failures and successes provide good opportunities for learning. Before moving on to new projects, allow enough time to gather the important lessons, and make sure those lessons are absorbed by your team. Also give the team the time to build skills, experiment, and learn about new tools and techniques. 

**Document operations.** Document all tools, processes, and automated tasks with the same level of quality as your product code. Document the current design and architecture of any systems you support, along with recovery processes and other maintenance procedures. Focus on the steps you actually perform, not theoretically optimal processes. Regularly review and update the documentation.

For code, make sure that meaningful comments are included, especially in public APIs, and use tools to automatically generate code documentation whenever possible. 

**Share knowledge.** Documentation is only useful if people know that it exists and find it. Ensure the documentation is organized and easily discoverable. Be creative: Use brown bags (informal presentations), videos, or newsletters to share knowledge.

## Development

**Provide developers with production-like self-service environments.** If development and test environments don't match the production environment, it is hard to test and diagnose problems. Therefore, keep development and test environments as close to the production environment as possible. Make sure that test data is consistent with the data used in production, even if it's sample data and not real production data (for privacy or compliance reasons). Plan to generate and anonymize sample test data.

**Instrument the application for insight.** To understand the health of your application, you need to know how it's performing and whether it's experiencing any errors or problems. Always include instrumentation as a design requirement, and build the instrumentation into the application from the start. Instrumentation must include event logging for root cause analysis, but also telemetry and metrics to monitor the overall health and usage of the application.

<!-- edit -->

**Track your technical debt.**
In many projects, release schedules can get prioritized over code quality to one degree or another. Always keep track of when this occurs. Document any shortcuts or other non-optimal implementation that have made their way into your code during the development process. Try to schedule time in the future to revisit and resolve these issues.

**All authorized stakeholders are able to provision infrastructure and deploy production-like systems.**
Setup of production resources and deployment of applications should not involve complicated manual tasks or detailed technical knowledge of the specific systems involved. Build tools so that anyone with the permissions to create or deploy production-like resources can do so without direct technical assistance from operations.

**Push updates directly to production .**
In order to reduce overall release cycle time, consider pushing properly tested code commits directly to production, using feature toggles to control enabled features. This allows you to move from development to release quickly with toggles providing the ability to easily enable of disable features. This is also useful when performing tests such as canary releases where you want only a particular feature deployed to a small subsets of production environments.

## Testing

**Automate testing.**
Manually testing software is a tedious process, and is susceptible to human error. Use tools to automate common testing tasks and integrate these tools into your build processes. Automated testing ensures consistent test coverage and reproducibility. Unit testing should be used to test individual code components, integrated UI tests should be performed by an automated tool. In addition, Azure offers a number of development and test resources that can help you configure and execute testing.

**Test for failures.**
Test for failure conditions. If a system is unable to make a connection to a service, how does it respond? Is it able to recover when the service is available again? Fault injection testing should be a standard part of review on test and staging environments. When your test process and practices are mature, consider running these tests in production. 

**Test in production.**
A release process should not end with deployment to production. Test processes should be in place to ensure deployed code is working as expecting. 
For deployments that are infrequently updated, production testing should be scheduled as a regular part of maintenance.

**Automate performance testing to identify performance issues early.**
Automated functional testing integrated into your continuous delivery pipeline will prevent most outright errors and bugs. However, it may not detect performance problems which can be just as problematic to users, especially on cloud-based applications. Define acceptable performance goals for metrics like latency, load times, or resource usage, and then put in place automated testing tools as part of your CI/CD pipeline to make sure your application is meeting those goals.

**Perform capacity testing.**
Functional testing handled by standard automated build processes may not account for problems and performance issues due to scale or resource limitations. Always define what your maximum expected capacity and usage limits are, then test not only that your application can handle those limits, but also test what happens when those limits are exceeded. Capacity testing should be performed at regular intervals during both the dev/build cycle. 

**Continue capacity testing post-release.**
Plan to continue to test beyond the initial release. Perform performance testing any time updates are made to production code. Use historical data to fine tune your testing and determine what types of tests need to be performed.  

**Perform automated security penetration testing.**
Ensuring your application is secure is as important as testing any other aspect of functionality. Automated penetration testing should be a standard part of a build and deployment process. Schedule regular security tests and vulnerability scanning on deployed applications, monitoring for open ports, endpoints, and attacks. Keep in mind that automated testing does nto remove the need for in-depth hands on security review at regular intervals.

**Perform automated business continuity testing.**
As important as it is to have plans for backup, redundancy, and failover, it's equally important to test these plans to confirm they work. Develop tests of backup recovery, failover redirection, and large scale business continuity plans. Set up automated processes to perform these tests regularly.

## Release

**Automate deployments.**
Create processes to automate the deployment of software to test, staging, and production environments. Automation enables faster and more reliable deployments, and ensures you'll get a consistent deployment to any environment you want to support, removing the risk of human error during manual deployments. It also provides the benefits of scheduling releases for convenient times to minimize any effects of potential downtime.

**Use continuous integration.**
Continuous integration (CI) is the practice of merging all developer code into a central codebase on a regular schedule (preferably on every commit, but at the very least once a day), and then automatically performing standard build and test processes to ensure the code still works. This ensures multiple users can be working on a codebase at the same time without running into versioning problems with changes others are making to the codebase, and errors can be found as early as possible.

Consider adopting a trunk based development model when using a continuous integration process. When all developers agree to a single "trunk" to commit completed updates to, and a requirement that those commits never break the build, automated build and test processes become much more straightforward to create

**Consider using continuous delivery to build a full CI/CD pipeline.**
Continuous delivery (CD) takes the CI process a step further by implementing tests and review processes to ensure code is always in a ready-to-deploy state. Adding continuous deliver to create a full CI/CD pipeline will help you detect code defects as soon as possible, and ensures properly tested updates can be deployed in a very short time.

> Continuous deployment (not to be confused with continuous delivery) is an additional process that take the further step of automatically deploying any code updates that have passed through the CI/CD pipeline. Continuous deployment requires robust automatic testing and advanced process planning in addition to what is put in place for CI/CD, and may not be appropriate for all teams.

**Make small incremental changes.**
The larger the size/scope of a particular code change, the larger the potential impact for any bugs introduced by that change. Whenever possible keep changes small. This not only limits the potential effects of changes, but makes understanding and debugging any issues much easier. 

**Control exposure to changes.**
Make sure you're in control of when updates are visible to your end users. Feature toggles are an important technique to control delivery of features.

**Implement appropriate release management strategies to reduce deployment risk.**
Deploying application updates to production always entails at least some risk. To minimize this risk, use release management strategies like canary releases or blue-green deployments to only deploy updates to a subset of your infrastructure and users. Once you've confirmed all is working as expected, you can roll the update out to the rest of your system.

**Document all changes.**
Minor updates and configuration changes can be a source of confusion and versioning conflict. Always keep a clear record of all changes you make to any of your systems, no matter how small. All changes should be logged, including patches applied, policy changes, configuration changes, etc...

**Make changes visible to the entire team.**
Changes in your system should be logged, and the records of changes visible to your entire team. This may not mean that all details are recorded, but that team members can see that a change occurred, and the change was to a specific item by a specific user at a specific time. For instance, a record of a credential change might not record the actual credentials data, but the type of change and who made the change should be recorded.

**Automate Deployments.**
Deployment should be automated and have systems in place to detect issues with live site health during rollout. Make sure all automated deployments include a mitigation process for preserving the existing code and data in production before the update replaces them in all production instances. There also needs to be an automated way to roll forward fixes or rollback changes to restore quality of service.

**Consider making infrastructure immutable.**
Building immutable infrastructure can be a key way to reduce cycle time and improve your deployment processes. When describing immutable infrastructure, "Cattle vs. Pets" is a commonly used analogy to make clear what immutable infrastructure provides. Pets are important to us and will be treated with care to make sure they stay healthy. Cattle are useful to us, but easily replaceable if they become sick or otherwise are no longer useful.

"Pets", in this sense, are indispensable servers and network devices that need to be kept online. These require patching and regular minor updates in hosting environments, usually done manually. Pets require extra monitoring and effort to prevent minor differences between test, dev, and production environments, which can make tracking the cause much more difficult. "Cattle" are the machines in cluster which are configured through automated tools and are part of fault tolerant systems. No individual machine is irreplaceable, as new ones can be spun up to replace old ones easily. 

Immutable infrastructure provides a way to build and manage the "Cattle" components of your systems. It works by replacing entire servers as part of any new deployment. This allows code updates and server upgrades are managed as a block, so that the deployment and its hosting environment are tested and deployed as a block. 
Once deployed, the infrastructure components aren't modified until the next build and deploy cycle, making ongoing patch and update tracking unnecessary. 

## Monitoring

**Make systems observable.**
Operations should always have clear visibility into the health and status of a system or service. Setup external health endpoints to monitor status, and ensure applications are coded to instrument the operations metrics as well as logs. Use a common and consistent schema that enables the correlation of events across systems. Azure Diagnostics and Application Insights are the standard method of tracking the health and status of Azure based resources. Microsoft Operation Management Suite also provides centralized monitoring and management for cloud or hybrid solutions.

**Aggregate and correlate logs/metrics to provide a real-time view of the system.**
A properly instrumented telemetry system will provide a large amount of raw event log and performance metrics data to sort through. Quickly troubleshooting issues and improving the application overall depends on processing this information in a way that provides insight into the current state of your application. Make sure telemetry and log data is processed and correlated in a short period of time, so that operations staff can always get an up-to-date picture of system health. Organize and display data in ways that present a cohesive view of any issues, so that whenever possible it's clear when events are related to one another.

Note that you should consult with your corporate retention policy for requirements on how data is processed and how long it should be stored. 

**Implement and tune automated alerts and notifications.**
Make sure performance issues and errors get noticed right away, and the right people are notified as soon as possible. Set up monitoring tools like Azure Monitor to detect patterns or conditions indicating potential or current issues in the system, and send alerts or notifications to the team members who can address the issues. Tune these alerts so that your detection process avoids false positives and make tuning and refining these notifications and ongoing process.

**Monitor assets and resources for expirations.**
Some resources and assets, for instance certificates, expire after a given amount of time. Make sure to track what assets expire, when they expire, and what services or features depend on them. Use automated processes to monitor these assets, and notify operations when they are scheduled to expire and escalate when expiration threatens to interrupt application functionality.

## Management

**Automate operations tasks.**
Manually handling repetitive operations processes can result in oversight and errors. Automate these tasks whenever possible to ensure consistent execution and quality. Keep the code handling this automation versioned under source control management system. As with any other code you create and maintain, automation tools should go through regular testing cycles.

**Use an Infrastructure as Code approach to provisioning.**
Minimize the amount of manual configuration that is needed to setup devices, applications, or processes. Use scripts and templates whenever possible to automate the provisioning of infrastructure. These scripts and templates should be maintained in a source control management system, like any other code you maintain. Azure Resource Manager templates allow you to create and deploy almost any type of Azure infrastructure resource through JSON-based code.

**Consider using containers.**
In a DevOps context, containers are a technology that provides a standard package based interface for deploying applications. Applications get deployed to containers using self-contained packages, which contain any software, dependencies, and files needed to run the application, greatly simplifying the deployment process.

Containers create an abstraction layer between the application and the underlying operating system, which provides consistency across environments and reduces issues related to moving an application form one environment to the next. This abstraction can also isolate a container from any other processes or application running on a host. 

**Implement resiliency and self-healing .**
Your systems need to handle many types of failures, from an individual service level all the way up to datacenter or region disruptions. Building in resiliency will improve your application's performance and increase consumer satisfaction. Make sure your code is implemented so that requests that are affected by short term outages are retried. Have auto-scaling configured for your services and have redundant resources available to fallback on during outages. Instrument your applications so that issues are reported immediately and you can manage outages or other system failures.

**Have an operations manual and complete support documentation in place.**
An operations manual (also called a RunBook) contains the procedures, tasks, and management information needed for operations staff to maintain a system. It’s also important to document any operations scenarios and mitigation plans that might come into play during a failure or other disruption to your service. Create this documentation during the development process, and keep it up to date after development is complete. This is a living document, and should be reviewed, tested, and improved regularly. 

Shared documentation is critical to handling operations issues efficient, and your DevOps practices should always encourage team members to contribute and share knowledge. The entire team should have access to documents, and the entire team should be able to help keep documents updated.

**Create shared documentation for on-call procedures.**
On-call is vital to supporting systems and applications off-hours. Make sure on-call duties, schedules, and procedures are documented and shared to all team members. Keep this information up-to-date at all times.

**Use configuration management.**
Configuration changes should be planned, visible to operations, and a record of all updates maintained. This management could take the form of a configuration management database, or a configuration as code approach. Configuration should be audited regularly to ensure what's expected is what's actually in place.

**Get an Azure support plan and understand the process.**
Azure offers a number of support options. Make sure you've signed up for the right plan and that your entire team knows how to use it. Team members should understand the details of your support plan, how the support process works, and how to open a support ticket with Azure.

**Document support escalation procedures for 3rd party dependencies.**
If any part of your application depends on external 3rd party services that you don't directly control, you need to have a plan to deal with outages. Create documentation for you planned mitigation processes, support contacts, and escalation paths.

**Follow least-privilege principles with auditing when granting access to resources.**
Make sure you carefully manage access, following good security principals. Make sure access is denied by default unless a user has explicitly been given access to a resource. Only grant a user access to what they need to complete their tasks. Track user permissions and perform regular security audits. 

**Use a bug tracking system for tracking issues.**
Without a system to organize the status and details of bugs or application issues, it's easy for items to get missed, work to be duplicated or additional problems introduced. Don't rely on casual person-to-person communication to track the status of bugs. Use an issue tracking tool to record details about problems, assign resources to address them, and provide an audit trail for the issue's status. 

**Automate access management.**
Assigning user accounts and access to resources should not be a manual process. Use an identity and access management (IAM) system like Azure Active Directory to centrally manage permissions and roles applied to resources and applications. 

**Manage all resources in a change management system.**
All aspects of your DevOps process should be included in a management and versioning system, so that changes can be easily tracked and audited. This involves each of the following types of resources:

- Code 
- Infrastructure 
- Configuration 
- Documentation
- Scripts 

The approach of treating all these types of resources as code carries through to the test / build / review process. 

**Use checklists.**
Create and use operations checklists to ensure processes are followed. It’s common to miss something in a routine manual, and following a checklist can force attention to details that might otherwise be overlooked. Keep your checklists maintained, and always be on the lookout for ways to further automate tasks and process currently performed manually.


