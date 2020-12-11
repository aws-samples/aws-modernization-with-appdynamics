+++
title = "Scale"
chapter = false
weight = 2
+++

![image](/images/modernize/ad_team_developer.png)


## Servers and Containers - EKS

When Nathan and his team selected EKS as the container orchestration engine of choice, they chose to create a multi-node cluster to scale up the service tiers that needed improved performance and greater throughput. 

**1 .**  Navigate back to the modernized version of the AD Financial APM (**App Performance Monitoring**) application and open it.

**2 .**  Click the **Servers tab** on the left-hand sidebar where you can see there are now 2 hosts along with their resource metrics such as CPU, Memory, and I/O.

**3 .**  Drill into one of the servers by double clicking on the server name and notice the improved load average while the CPU utilization remains modest.

![image](/images/modernize/servers_00.png)

![image](/images/modernize/servers_01.png)

**1 .**  Navigate over to the left-hand menu and click on Containers. 

Each of the servers is hosting a container in support of the tiers that have been scaled out such as AccountManagement, BalanceServices, PerLoanServices, etc. This will ensure better reliability since the application tiers are now balanced across two different hosts. This view allows us to quickly identify the key performance metrics of each container. Using built-in health rules, if performance starts to degrade, AppDynamics can send out email alerts, send HTTP alerts to any alert management system and even perform an action to proactively prevent an outage or user impacting event.

![image](/images/modernize/containers_00.png)

{{% notice info %}}
**EKS observability deep-dive coming up next** in the **Operate** section, featuring the **Cluster Agent**.
{{% /notice %}}

<br>

## Remote Services - S3

In addition to the flow map reflecting all of the changes in the real time topology of the application, we can view Remote Services to show the detailed metrics of the calls to the new secure storage solution, S3. 

**1 .**  Click on **Remote Services** on the left menu.

**2 .**  Notice the sub-second response time for all the S3 calls.

You can read more about Remote Services <a href="https://docs.appdynamics.com/display/latest/Remote+Services" target="_blank">**here**</a>

![image](/images/modernize/remote_services_00.png)

<br>

## Databases - RDS

The native MySQL database used in the pre-modernized version of the application was straining to keep up with the demand of the application load.  Let's take a look at how much better the new AWS RDS MySQL database is performing.

**1 .**  Navigate to the database named like **&lt;your_lab_user_name&gt;-AD-Fin-PostMod**

**2 .**  Click on the colored health status circle to see details of the server health

**3 .**  Observe the total time spent executing SQL statements during the specified time period

**4 .**  Observe the total number of executions during the specified time period

**5 .**  Hover over the time series on the chart to see the detail of the recorded metrics

**6 .**  Hover over the labels for each wait state to see a more detailed description

![image](/images/modernize/databases_00.png)


## Here's the Advantage

- Easily compare and validate the throughput and resource usage of the hosts and containers in the application
- Quickly observe the availability and performance of the cloud services within the application context
- Understand database performance in detail to validate improvements after modernizing with RDS


## Next <i class='fas fa-cog fa-spin'></i>

In the next section we'll examine how AppDynamics **Business iQ** provides **deep visibility into key real-time business metrics** correlated to application performance.


<!---
{{% notice warning %}}
The Cloud9 workspace should be built by an IAM user with Administrator privileges,
not the root account user. Please ensure you are logged in as an IAM user, not the root
account user.
{{% /notice %}}
-->

<!---
{{% notice info %}}
This workshop was designed to run in the **Oregon (us-west-2)** region. **Please don't
run in any other region.** Future versions of this workshop will expand region availability,
and this message will be removed.
{{% /notice %}}
-->

<!---
{{% notice tip %}}
Ad blockers, javascript disablers, and tracking blockers should be disabled for
the cloud9 domain, or connecting to the workspace might be impacted.
Cloud9 requires third-party-cookies. You can whitelist the [specific domains]( https://docs.aws.amazon.com/cloud9/latest/user-guide/troubleshooting.html#troubleshooting-env-loading).
{{% /notice %}}
-->
