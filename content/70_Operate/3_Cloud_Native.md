+++
title = "Cloud Native"
chapter = false
weight = 3
+++

![image](/images/operate/ad_team_cloudops.png) 

Cloud Native Visualization introduces the AIOps platform to visualize the interactions and relationships of objects in your application infrastructure. This capability helps improve collaboration and unify the efforts of different engineering functions by creating a real-time single source of truth for monitoring your application environment.  Get immediate insights into cloud deployments with AppDynamics' Cloud Native Visualization functionality and deliver deep value for your business, right out of the box.  

Quickly resolve issues impacting the user experience caused by microservice architectures and cloud native technologies new to your enterprise.  The Cloud Native visualizations, metrics, and meta-data, build upon the existing AppDynamics Flow Map visualizations and APM telemetry, by combining and correlating both, to achieve a comprehensive level of insight within a single platform. 

{{% notice info %}}
As of this this workshop, the Cloud Native feature was recently released. For demonstration purposes, you will be accessing a separate application in the AppDynamics controller that has already been enabled with the Cloud Native feature.
{{% /notice %}}

This illustration shows a high-level overview of Cloud Native Visualization:

![image](/images/operate/cloud_native_arch.png)

## Navigate to the Cloud Native APM Application

Let's start by finding the AD Financial APM (**App Performance Monitoring**) application that has been **enabled for Cloud Native** and open it.

**1 .**  Click on the **Home** option on the top menu.

- In the **Applications** tile, you should see the application named **AD-Financial_Cloud-Native**

**2 .**  Click on the application name to drill into the flow map view for the application.

![image](/images/operate/open_apm_app.png)


**1 .**  From the application dashboard **click on the location Pin** to the right of the time range.

![image](/images/operate/open_cloud_native.png)


## Applications Perspective

**1 .**  The **Filter by feature** in Cloud Native Visualization is available for all entities displayed on the object page or Relationships map. The available filters are:

- **Availability Zone (AZ):** An Availability Zone, within a region, offers one or more unique data centers with redundant power, networking, and connectivity in a region to ensure resilience. 
- **Region:** AppDynamics displays the concept of Regions, physical locations where data centers are geo-located to help businesses determine the correct geography for data compliance, service availability, and pricing.
- **VPC:** Virtual Private Clouds contain multiple availability zones.


**2 .**  The **Relationships area** allows users to navigate the vertical layers of entities that make up your application. 

- At the highest level is **Applications**, under Applications are **Business Transactions**, then **Services**, **Hosts**, **Databases**, and other relevant associated infrastructure entities. In the Relationships area, if you click on any object, content is updated within the context of that object. 
- Different types of entities **appear in the Relationships area depending on the entity you are viewing**. For example, Service Instances are not displayed on the Relationships area when looking at Applications. 
- Service Instances appear when you reach the level of Services. If hosts and databases are not associated with an application, then those layers do not show.

**3 .**  The **Lists view** is shown in the main content area. The Lists view **displays a list of multiple instances of one entity type**. 

- In this case, the entity type is Applications. 

**4 .**  The **Details view** shows Key Performance Indicator (KPI) metric trends based on the object page context.

**5 .**  Click on the **BizLoan-Services** entity to see the details of this entity.

![image](/images/operate/cloud_native_00.png)

{{% notice info %}}
You may need to try using a different browser if you're not seeing all the metrics and details as seen in the example images.
{{% /notice %}}

## Services Perspective

**1 .**  The **Interactions map** is shown in the main content area.

- The Interactions map is a graph that represents how **services, databases, hosts, and other associated infrastructure entities within a business transaction**, interact with each other. 
- You can **measure the entities' performance and track the origin and the destination of these interactions** to trace a sequence of requests through your application.
- In this example you can see the **Account-Management** service making requests to **BizLoan-Services** and **how those requests branch out to the other backend entities** handling those requests.

**2 .**  Next let's navigate back to the application level view by clicking on the **AD-Financial_Cloud-Native** link on the top left. 

![image](/images/operate/cloud_native_01.png)


## Business Transactions Perspective

**1 .**  Click on the **Business Transaction** circle in the Relationships area.

**2 .**  Click on the **/rest/loanUnderwritingComplete** Business Transaction.

![image](/images/operate/cloud_native_02.png)


From here we can **see all of the services and AWS components involved in this business transaction**. AppDynamics has **automatically correlated the business logic with the cloud services** and components involved. 

**1 .**  Click on the database on the right **to see the details of the RDS MySQL instance**.

![image](/images/operate/cloud_native_03.png)


## Databases Perspective

**1 .**  Explore the KPI's collected for the database.

**2 .**  Explore the properties listed on the right.

![image](/images/operate/cloud_native_04.png)


## Hosts Perspective

**1 .**  Click on the **AD-Financial_Cloud-Native** link to go back to the applications view.

**2 .**  Click on the **Hosts** circle, then select one of the hosts.

**3 .**  Explore the KPI's collected for the host.

**4 .**  Explore the properties listed on the right.

**5 .**  Once you're done exploring the Cloud Native dashboards, click on the exit icon.


![image](/images/operate/cloud_native_05.png)


## Related Resources

&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate'></i></span>&nbsp; <a href="https://www.appdynamics.com/solutions/cloud/cloud-monitoring/what-is-cloud-native-architecture" target="_blank">**What is cloud native architecture**</a>

&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate'></i></span>&nbsp; <a href="https://www.appdynamics.com/resources/ebook/hybrid-cloud-application-performance-playbook" target="_blank">**The Hybrid Cloud Application Performance Playbook**</a>



## Next <i class='fas fa-cog fa-spin'></i>

We'll **summarize what we've learned** and **start wrapping up the workshop!** 


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



