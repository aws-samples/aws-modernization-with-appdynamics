+++
title = "End User Monitoring"
chapter = false
weight = 3
+++

![image](/images/mobilize/ad_team_architect.png)


#### The first few challanges Nathan and his team need to address are related to the web frontend

- Differentiating issues in the web UI versus the backend services
- Mapping the web pages to the backend business transactions
- Baselining the end user experience on the web site with:
  - End User Response Time
  - Drop-off rates in the user journey

## Navigate to the BRUM Application

Once you have logged into the AppDynamics controller, you should see the home page. Let's start by finding the pre-modernized version of the AD Financial BRUM (**Browser Real User Monitoring**) application and open it using the steps below.

**1 .**  Click on the **Home** option on the top menu.

- In the **User Experience** tile, you should see the application named like **&lt;your_lab_user_name&gt;-AD-Fin-PreMod-Web**

**2 .**  Click on the application name to open the Overview Dashboard for the application.

![image](/images/mobilize/open_brum_app.png)


## Browser App Dashboard

The Browser App Overview dashboard displays a set of configurable widgets. 

**1 .**  The dashbaord shows **key high-level indicators of web application performance**, including:

- Page Requests per Minute
- End User Response Time Trend and Distribution
- Total Page Requests by Geo
- End User Response Time by Geo
- Top 10 Browsers and Devices
- Top 5 Pages and Countries by Total Requests

You can read more about the Browser Application Overview dashboard <a href="https://docs.appdynamics.com/display/latest/Browser+App+Dashboard" target="_blank">**here**</a>

**2 .**  Take a moment to explore the:

- **Geo Dashboard**
  - You can read more about the Browser Application Geo dashboard <a href="https://docs.appdynamics.com/display/latest/Browser+App+Dashboard#BrowserAppDashboard-geo" target="_blank">**here**</a>
- **Browser Snapshots**
  - You can read more about the Browser Snapshots <a href="https://docs.appdynamics.com/display/latest/Browser+Snapshots" target="_blank">**here**</a> and <a href="https://docs.appdynamics.com/display/latest/Page+Browser+Snapshots" target="_blank">**here**</a>
- **Usage Stats**
  - You can read more about the Browser Application Usage Stats dashboard <a href="https://docs.appdynamics.com/display/latest/Browser+App+Dashboard#BrowserAppDashboard-usage-stats" target="_blank">**here**</a>


**3 .**  Click on the **Pages & AJAX Requests** on the left to get a **breakdown of metrics for each web page including End User Response Time**.

![image](/images/mobilize/brum_app_01.png)


## Pages & AJAX Requests

We want to identify the web pages that are having errors and or poor end user response times so we can focus and prioritize them if needed.

**1 .**  Sort the list of web pages by the highest end user response time.
- Notice that we see **5 pages with the highest response times**, all of them **related to the loan approval process**

**2 .**  We can tell right away that the **high response times** are **mostly due to the First Byte Time (ms) metric**
- Though the **DOM Ready Time (ms) metric shows higher timings** than **the First Byte Time (ms) metric**, we'll explain in the next step **why the former metric is more revealing**
  
**3 .**  Double-click on the **www&#46;ad-financial&#46;com&#47;&#47;loanverifydocumentation** page so we can look at the detailed timing breakdown for that page

![image](/images/mobilize/brum_app_02.png)

## Base Page Dashboard

The Base Page Dashboard shows you how a web page has been performing over time, within the context of the time range you have selected to view.

**1 .**  At the top of the Base Page dashboard you will see key performance indicators, End User Response Time, Load, Cache Hits, and Page Views with JS errors across the period selected in the timeframe dropdown from the upper-right side of the Controller UI. Cache Hits indicates resources fetched from a cache, such as a CDN, rather than from the source.

**2 .**  In the Timing Breakdown section you will see a waterfall graph that displays the average times needed for each aspect of the page load process. For more information on what each of the metrics measures, hover over its name on the left. A popup appears with a definition. For more detailed information, see <a href="https://docs.appdynamics.com/display/latest/Page+and+IFrame+Dashboards" target="_blank">**Browser RUM Metrics**</a>

![image](/images/mobilize/brum_app_03.png)

The **First Byte Time metric is important** since it **tells us how much time was taken from when the page was requested, until the initial part of the response was received** from the server or backend.  This indicates that **the majority of slowness for this page is happening on the server side**.  

We can see in this example that **network latency was an insignificant part** of the total response time.  We can also see in the waterfall view that the **time taken to process the response after it was received and render the page was a small portion** of the total time.

You can **investigate the other 4 web pages related to the loan approval process** to validate **the majority percentage of their high end user response times is happening on the backend**.

## Business Transaction Correlation

AppDynamics **automatically correlates the specific business transactions** on the server side that are **accessed by the Web Page and the AJAX Requests and iFrames within the page**.  This valuable feature **allows you to easily map out the dependencies between the frontend and the backend**.

**1 .**  Use the scroll bar on the right to scroll down until you see the **Related Business Transactions** section.

**2 .**  We can see that this web page is accessing the **/rest/loanVerifyDocumentation** business transaction.

**3 .**  Now click on the **Browser Snapshots** tab to see individual requests for this web page.

![image](/images/mobilize/brum_app_04.png)


## Browser Snapshots

AppDynamics automatically captures detailed data on each end user request to a web page as well as capturing the entire session containing the path each end user took through the web site. Here we will look at an example of a single end user page request to show you how AppDynamics automatically correlates the entire flow of an end user request.

**1 .**  Sort the browser snapshots on the column named **Has Server Snapshot**.

**2 .**  Double-click on the browser snapshot that has a associated server snapshot.

![image](/images/mobilize/brum_app_05.png)

You can see that the browser snapshot shows the same waterfall timing breakdown and we notice once again that the majority of the time is spent waiting on the backend to fulfill the request.

![image](/images/mobilize/brum_app_06.png)

**1 .**  Use the scroll bar on the right to scroll down until you see the associated **Server Snapshot**.

**2 .**  Double-click on the server snapshot to follow the path of the user request to the backend to see why this web page request had such a high response time.

![image](/images/mobilize/brum_app_07.png)

You can drill down through the entire path of the transaction with the server side snapshot to quickly find root cause.  We'll explore server snapshots in more detail when we cover the upcoming section on Business Transactions.

![image](/images/mobilize/brum_app_08.png)


## Experience Journey Map

The **Experience Journey Map provides real-time insights** into application and business performance, **visualizing key user journeys** and the **correlation between performance and traffic**. This perspective **unifies all application stakeholders**, application owners, developers, and IT operations.

**1 .**  Click on the **Experience Journey Map** on the left to see how **AppDynamics automatically maps out the journey** that users take through the browser application.

From here we can see the path of the **loan approval process** to understand:

- the numer of requests for each stage and page in the process flow
- the performance of each stage and page in the process flow
- the drop-off rate from page to page in the process flow

![image](/images/mobilize/brum_app_09.png)


<!-- 

The **Experience Journey Map provides real-time insights** into application and business performance, **visualizing key user journeys** and the **correlation between performance and traffic**. This perspective **unifies all application stakeholders:** application owners, developers, and IT operations.

From here we can see: 

**1 .**  The path of the **loan approval process** to understand:

- the numer of requests for each stage and page in the process flow
- the performance of each stage and page in the process flow
- the drop-off rate from page to page in the process flow

**2 .**  Click on the **loanunderwritingcomplete** page

![image](/images/mobilize/brum_app_02.png)

<br>

Drilling into the **loanunderwritingcomplete** page shows us:

- The total user visits from all sources
- The total user visits from the top incoming source
- The drop-off rate from the prior page to this page

**1 .**  Click here to expand the **details for the incoming traffic** 

**2 .**  Click here to expand the **details for the outgoing traffic**

![image](/images/mobilize/brum_app_03.png)

<br>

For here we can see the **performance breakdowns** for **each traffic source**:

**1 .**  The incoming traffic from the **loancreditcheck** page **shows issues with a large percentage** of **slow and very slow requests**.

**2 .**  The outgoing traffic to the **loanapproved** page **shows issues with almost 100%** of **very slow requests**.

![image](/images/mobilize/brum_app_04.png)

<br>

To see more detail about the traffic from the **loancreditcheck** page to the **loanunderwritingcomplete** page:

**1 .**  Click here to bring up the detail panel for the traffic between the **loancreditcheck** page and the **loanunderwritingcomplete** page.

**2 .**  Review the detailed description of state of the traffic from the **loancreditcheck** page.

**2 .**  Expand the **details of the slow requests** to view the **breakdown of browsers and devices used to make the requests**.

![image](/images/mobilize/brum_app_05.png)  -->


## Here's the Advantage

- Identify and **take action on critical issues** with the frontend to **optimize end user experience**.
- **Aggregate and display user journeys** to **understand the most frequent paths** through the application.
- Understand the **mapping of dependencies** between **the components of the frontend and the backend business transactions they utilize**.


{{% notice info %}}
All the dashboards and the browser snapshot views seen in this section are provided OOTB and the content they contain is real-time, dynamic, and reflects the data gathered from the AppDynamics Browser Real User Monitoring Agent.
{{% /notice %}}

## Takeaways

- We've **identified the 5 web pages** related to the loan approval process **having issues**
- We have proved **the degraded end user response response times** for those pages **are backend related**
- We now have an **accurate mapping** of those **pages to the backend business transactions**
- We've **documented the drop-off rates** for each stage **of the loan approval process**

## Next <i class='fas fa-cog fa-spin'></i>

In the next section **we'll use AppDynamics Flow Maps** to dive deeper and **gain valuable insights into the backend systems that service the frontend**.


<!---
{{% notice warning %}}
The Cloud9 workspace should be built by an IAM user with Administrator privileges,
not the root account user. Please ensure you are logged in as an IAM user, not the root
account user.
{{% /notice %}}
-->

<!---
{{% notice note %}}
This workshop was designed to run in the **Oregon (us-west-2)** region. **Please don't
run in any other region.** Future versions of this workshop will expand region availability,
and this message will be removed.
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
These key metrics become even more valuable over time with deeper insights into the usage patterns 
{{% /notice %}}


{{% notice tip %}}
Ad blockers, javascript disablers, and tracking blockers should be disabled for
the cloud9 domain, or connecting to the workspace might be impacted.
Cloud9 requires third-party-cookies. You can whitelist the [specific domains]( https://docs.aws.amazon.com/cloud9/latest/user-guide/troubleshooting.html#troubleshooting-env-loading).
{{% /notice %}}
-->
