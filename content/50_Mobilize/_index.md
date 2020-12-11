+++
title = "Mobilize"
chapter = false
weight = 50
+++


#### Nathan is the Lead Architect for the modernization project at AD Financial. &nbsp; Nathan was instrumental during the initial migration of the first set of applications from the data center to AWS. &nbsp; Nathan understands the complexities and risks of moving and modernizing large production workloads and relies on the strategies, practices, and tools that have proven their value, leading to success.

![image](/images/mobilize/ad_team_architect.png)

{{% notice info %}}
The Mobilize, Modernize, and Operate sections of the workshop build upon the workshop setup by walking the user through the AppDynamics UI Dashboards.
{{% /notice %}}

In the past, **IT teams had to create architecture diagrams for each application** across their enterprise landscape.  These **quickly became obsolete and out-of-date** as teams struggled to keep pace **with the continual changes being made to the frontends and backends** of their applications.

With AppDynamics, there's **no need to keep manually creating and updating architecture diagrams** for your application. **AppDynamics provides you with end-to-end OOTB dynamic visual representations** for all the **web pages, mobile views, components, services, hosts, backends, and depencies of your monitored application**, all in direct context of the time frame you select.  

<br>

When AD Financial first migrated its customer facing web application to AWS, Nathan had the AppDynamics advantage that assisted him and his team throughout the entire migration process.  

**Utilizing AppDynamics, Nathan and team can efficiently and effectively:**
- perform detailed application discovery
- perform detailed application dependency analysis
- priortize services to refactor
- gather application baselines
- create a viable modernization plan




## Frontend Architecture

AppDynamics **End User Monitoring (EUM)** gives you deep **visibility on the performance of your web and mobile applications**. EUM helps you troubleshoot problems such as slow web, Ajax, mobile network requests, or IoT application errors. EUM provides metrics on application performance and user activity, such as:

- How server performance impacts your web, mobile, and device performance
- How third-party APIs impact your web, mobile, and device performance
- Where your heaviest loads originate
- How your users connect to and navigate your application

The **AppDynamics Experience Journey Map** provides a dynamic up-to-date view of your application frontend and maps out the pages, views, and actions and the path end users navigate through the frontend.

![image](/images/mobilize/brum_app_00.png)


## Backend Architecture

The **AppDynamics Flow Map** goes far beyond a basic architecture diagram.  

It provides you **much more than just "an inventory list"**, such as:

 - **The response time**:
   -  for the whole application
   -  for each service
   -  between each service
   -  to each dependency
 - **The calls per minute**:
   - for the whole application
   - for each service
   - between each service
   - to each dependency
 - **The errors per minute**:
   - for the whole application
   - for each service
   - between each service
   - to each dependency

![image](/images/mobilize/01_flowmap.png)

{{% notice info %}}
**Optional:**  You can explore the artifacts that were utilized to deploy the application and AppDynamics agents associated with this section by navigating to the following directories listed below that are located on your Cloud9 instance: 
{{% /notice %}}

```
/home/ec2-user/environment/deployment

/home/ec2-user/environment/deployment/pre-mod-docker
```

## Next <i class='fas fa-cog fa-spin'></i>

Let's **follow Nathan and his team** as they **utilize AppDynamics to perform a detailed analysis** of the following **aspects of the pre-modernized application** in its current state:

- Differentiate issues in the web UI versus the backend services that support it
- Identify all application components, the hosts they run on, and their resource utilization
- Identify all dependencies to backends and dependencies across service APIs
- Identify transactions associated with loan processing that would be effected when decoupling services
- Identify the path those transactions take through the system with all components involved to map them out
- Identify specific components that are causing performance degradation of key business transactions

