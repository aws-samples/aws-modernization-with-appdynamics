+++
title = "Accelerate"
chapter = false
weight = 1
+++

![image](/images/modernize/ad_team_developer.png)

Once the new architectural components were selected, Nathan, the architect we met earlier, worked with Alex and his team to take advantage of AppDynamics to once again see the real time topology of the application. Not only did this allow the teams to quickly understand all of the differences in terms of the application components, but it also enabled them to get immediate insight into how much better the overall application performance was after the modernization effort was completed.

<br>

## Navigate to the Modernized APM Application

Let's start by finding the modernized version of the AD Financial APM (**App Performance Monitoring**) application and open it to investigate the flow map.

**1 .**  Click on the **Home** option on the top menu.

- In the **Applications** tile, you should see the application named like **&lt;your_lab_user_name&gt;-AD-Fin-PostMod**

**2 .**  Click on the application name to drill into the flow map view for the application.

![image](/images/modernize/open_apm_app.png)

<br>

## Application Level Flow Map

You can now see that AppDynamics shows an updated flow map that reflects the new components utilized such as the S3 remote services. Since the application team is now benefitting from the advanced container management capabilities of EKS, they were able to easily scale out many of the tiers as shown by the number of nodes inside the green circle. If you look back at the pre-modernized version of AD Financial you will see only 1 node supporting each tier. This was another risk that was addressed since there were multiple single points of failure prior to the modernization.

**1 .**  S3 buckets used to archive audit data are automatically detected, mapped, and performance recorded.

**2 .**  With EKS, increasing the number of nodes/pods for a service tier becomes a simple task, achieved within minutes.

![image](/images/modernize/flowmap_00.png)


<br>

**1 .**  Notice that we **now have separation** for the tiers **supporting the Business and Personal Loan services**.

**2 .**  Notice the **dramatic improvement of the transaction performance** compared to the pre-modernized version of the application.

**2 .**  We can see that the **average response time has substantially decreased** even as the **load has almost doubled** in comparison.

![image](/images/modernize/flowmap_01.png)

<br>

## Business Transactions

Earlier we identified that the business transactions associated with loan servicing that should be prioritized during modernization. It is critical that we optimize the performance for those key business transactions. Let’s now take a look at those same business transactions and see how their performance has changed.

**1 .**  Click on the **Business Transactions** option on the left menu.

**2 .**  Review the **improved response times of** the **key business transactions associated with loan servicing**.

There has now been significant improvement in the average response times of these critical transactions associated with loan processing. We also see that far less of these individual transactions are being graded as slow or very slow as shown by the percentages in the table. Recall that AppDynamics will count, measure and score every single business transaction against a learned dynamic baseline. This is paramount to empower a team to quickly see when certain transactions are degrading and performing poorly.

![image](/images/modernize/biz_txns_00.png)

<br>

## Navigate to the BRUM Application

Next let's go to the post-modernized version of the AD Financial BRUM (**Browser Real User Monitoring**) application and open it using the steps below.

**1 .**  Click on the **Home** option on the top menu.

- In the **User Experience** tile, you should see the application named like **&lt;your_lab_user_name&gt;-AD-Fin-PostMod-Web**

**2 .**  Click on the application name to open the Overview Dashboard for the application.

![image](/images/modernize/open_brum_app.png)

<br>

We can observe the performance increase seen for the pages associated with loan processing by following the steps below.

**1 .**  Click on the **Pages &#38; AJAX Requests** option on the left menu.

**2 .**  Notice that **the loan pages have much lower average response times** than the pre-modernized version of the application.

**3 .**  Double-click on the **loanunderwritingcomplete** page to see more detail about that web page.

![image](/images/modernize/brum_app_00.png)

<br>

From here you can understand the breakdown of the End User Response Time for this page.  The waterfall graph shown below displays the average times for the time frame selected for each aspect of the page load process. For more information on each of the metric measurements, hover over its name on the left. A popup appears with a definition of the metric.

You can read more about the Browser Page Timing Breakdown <a href="https://docs.appdynamics.com/display/latest/Page+and+IFrame+Dashboards" target="_blank">**here**</a>

![image](/images/modernize/brum_app_01.png)


## Here's the Advantage

- Get immediate insight to the improvement of the overall application performance as you refactor and modernize
- Instantly validate the availability and performance of application components and the cloud services they utilize
- Easily confirm that the critical business transactions are providing improved functionality and throughput across services


## Next <i class='fas fa-cog fa-spin'></i>

In the next section we'll look at **how the development team scaled the application** with the cloud services they utilized.


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



