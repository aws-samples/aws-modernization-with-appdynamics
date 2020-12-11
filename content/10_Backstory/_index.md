+++
title = "Backstory"
chapter = false
weight = 10
+++

![image](/images/the_backstory/ad_financial_logo_lrg.png)

#### AD Financial serves its customers with a full range of financial products and services through award-winning digital banking capabilities and a retail banking network across the globe with a focus on helping individuals navigate each stage of their financial lives, working with  large and small businesses to drive their success by providing award-winning service.

![image](/images/the_backstory/ad_financial_web.png)

<!--
AD Financial recently experienced a data breach in their online application, and while the breach was minimized, the source of the breach was never determined due to lack of granularity in the stored audit data.  The need for a replicated audit trail, containing more details of how the data was accessed, became immediately apparent.  The ingestion of audit data combined with loan application updates within the same DB instance could also be negatively impacting database performance. -->

AD Financial has experienced a surge in demand for home mortgage refinancing and small business loans over the past six months.  As a result, their web site and the backend services that support it have suffered from slower loan processing times while customer service has seen a rise in complaints from end users.  AD Financial fully intends to maintain its brand and position in the competitive financial market. The budget has been approved to proceed with the modernization project that will help the company retain its competitive edge and customer loyaly.  An initial assessment of the current web site and the loan processing services behind it revealed several areas that warrant further analysis.


##### &nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-xs'></i></span>&nbsp; Recent changes to the UI framework on the web site need review
##### &nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-xs'></i></span>&nbsp; Both personal and business loan services may be too tightly coupled
##### &nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-xs'></i></span>&nbsp; Collocation of loan data and audit data may be constraining the database
##### &nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-xs'></i></span>&nbsp; Current container services lack orchestration and scalability features

<br>

#### Avi is the Chief Technology Officer (CTO) for AD Financial and has tasked his team leads to assess the following challenges associated with the modernization effort:

![image](/images/the_backstory/ad_team_cto.png)



## 1: Understand the Current Application

It has been over a year since the Dev team refactored the online application, containerized the services and moved them out of the data center into the cloud.  There is no current architecture diagram for the application and many changes have been made since its original deployment. An accurate assessment of the items below are required so the team can create a viable modernization plan:

##### &nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-xs'></i></span>&nbsp; Differentiate issues in the web UI versus the backend services
##### &nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-xs'></i></span>&nbsp; Inventory of all application components, the hosts they run on, and their resource utilization
##### &nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-xs'></i></span>&nbsp; Inventory of all dependencies across service APIs
##### &nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-xs'></i></span>&nbsp; Inventory of all dependencies to backends and third-party systems
##### &nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-xs'></i></span>&nbsp; Inventory of all the teams associated with the different application components 

## 2: Understand Key Business Transactions

Once we have an inventory of the application components, services, and dependencies, we need to understand what the key business transactions are in the application and the components they map to so we can prioritize them for refactoring during our modernization effort.  For example, what are the transactions that access sensitive data and require auditing?  What are the key business transactions associated with services we want to refactor? To answer those questions, we need to understand the following:

##### &nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-xs'></i></span>&nbsp; What are the transactions associated with loan processing that would be effected when decoupling services?
##### &nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-xs'></i></span>&nbsp; The path those transactions take through the system with all components involved to map them out from start to finish.
##### &nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-xs'></i></span>&nbsp; What specific components are causing performance degradation of key business transactions:
##### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-minus fa-xs'></i></span>&nbsp; Web page issues?
##### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-minus fa-xs'></i></span>&nbsp; Code related issues?
##### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-minus fa-xs'></i></span>&nbsp; Database constraints?
##### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-minus fa-xs'></i></span>&nbsp; Infrastructure constraints?



## 3: Select the Appropriate Modernization Strategy

The landscape of new cloud services and technologies available today have made dramatic improvements in efficiency in recent years.  However, the services and technologies selected and adopted need to satisfy the business and engineering requirements while also promoting adoption across the different teams involved in the modernization effort.

To that end, the business:

##### &nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-xs'></i></span>&nbsp; Anticipates the need to scale and operate more efficiently due to growing demand and higher transaction rates
##### &nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-xs'></i></span>&nbsp; Looks to separate the storage and access of audit data to increase throughput and scale them independently  
##### &nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-xs'></i></span>&nbsp; Must reduce or eliminate downtime and service outages due to competing demands of reporting and loan submissions


## 4: Validate Performance and End User Experience

Validating the success of our modernization effort will be next to impossible without having an accurate understanding of what the application and business performance metrics are, as well as end user experience metrics, both pre-modernization and post-modernization.  Our CTO Avi, has recommended that we capture baseline data on the following indicators for the application, both pre and post modernization to validate our success:

##### &nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-xs'></i></span>&nbsp; Overall end user experience online
##### &nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-xs'></i></span>&nbsp; Business transaction performance
##### &nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-xs'></i></span>&nbsp; Component and service level performance
##### &nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-xs'></i></span>&nbsp; Business performance of the loan approval process

<!-- Consolidating metrics from the siloed tools used by the teams at various layers of the application takes too much time and effort and doesn’t scale well.  The current tools have no way of providing an end to end view of the entire application stack in its current form, nor would they give any visibility into the native cloud services like S3 and EKS.  Current tools also lack any capability of automatic baselines for performance and end user experience, at the application, business transaction, service, and component level. -->

## 5: Streamline Operations &#38; Minimize Risk

The challenges associated with large modernized enterprise applications in a virtual and dynamic cloud landscape can be complex. This is especially true for the operations team that manage those production applications.  Now they must support applications that utilize new cloud services and technologies they may not be familiar with.  The operations team recognizes that they need to realign their strategy and operational toolset to perform efficiently and effectively while staying within their budget.

Specifically, how can the operations team:

##### &nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-xs'></i></span>&nbsp; Be proactively alerted to pinpoint root cause before it affects the end user or impacts the business?
##### &nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-xs'></i></span>&nbsp; Get deep visibility into the new cloud native services being utilized by the application?
##### &nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #4e3eb1;"><i class='fas fa-certificate fa-xs'></i></span>&nbsp; Keep performing optimally while supporting new technologies without growing the size of the team?

<br>

## Next <i class='fas fa-cog fa-spin'></i>

Let's get started by **setting up the prerequisites** in your **AWS environment**.


<!-- **Distributed Architectures:** Microservices, containers, Kubernetes and the use of multiple AWS Availability Zones have created a more expansive and richer IT landscape.

- **Additional Dependencies:** APIs that connect to third-party services outside of the organization may not always perform as expected. The customer does not care who is at fault, they simply want a frictionless engagement with the applications.

- **Faster Release Cycles:** Release frequencies have shifted - to monthly, weekly, daily, or even hourly deployments. No matter how minor some releases may seem, they all have the potential to impact the customer experience.

Historically, monitoring has reflected the departmental nature of Development and IT Operations teams, who each used a tool for their area of responsibility, such as:

- Network
- Database
- Web
- Mobile
- Server

Proliferation of these tools has often led to:

- **Finger Pointing:** More time spent proving innocence vs. collaborating, results in slower Root Cause Analysis (RCA) and poor team collaboration.

- **Lack of Visibility:** No insight into end-to-end execution times, which causes “watermelon KPIs,” i.e. looks green, but users still struggle.

- **Suboptimal Prioritization:** Teams are unaware of the true business impact of what has occurred. 


The operations team needs to keep their end users happy and maximize revenue. AppDynamics helps ensure optimal user experience by measuring key performance metrics and reporting on any deviations in real-time. However, AppDynamics goes beyond alerts by pinpointing where an issue is occurring and providing AI-driven remediation recommendations. This capability is especially important to proactively identify potential issues before they result in degraded customer experiences and potential lost business.  -->