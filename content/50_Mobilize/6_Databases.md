+++
title = "Databases"
chapter = false
weight = 6
+++

![image](/images/mobilize/ad_team_architect.png)

#### In the previous section, the business transactions view helped us easily isolate the 5 problematic business transactions for the loan approval process.  We identified that significant time was spent in one of the JDBC calls to the database.  Let's now take a deeper look to isolate the specific database queries that are degarding the perfomance of the loan application process.

## DB Visibility from APM Agents

With AppDynamics APM agents, not only did we see database calls on the Flow Maps and in the Transaction Snapshots, but we also get a summary of the calls the application made to each database containing valuable KPIs.

**1 .**  Click on the **Database Calls** option on the left menu.

**2 .**  Notice the database that had the fewest calls yet had the highest average response times.

If we drilled in and looked at the snapshots for those database calls, we would see they were select queries related to audit data reporting.  Let's use the AppDynamics Database Agent to confirm these queries are consuming the most database resources. 

![image](/images/mobilize/database_00.png)


Database Visibility in AppDynamics provides end-to-end visibility on the performance of your database, helps you troubleshoot problems such as slow response times and excessive load, and provides metrics on database activities, such as:

- SQL statements or stored procedures that are consuming most of the system resources
- Statistics on procedures, SQL statements, and SQL query plans
- Time spent on fetching, sorting, or waiting on a lock
- Activity from the previous day, week, or month


## Navigate to the Pre-Modernized Database

Let's start by finding the pre-modernized MySQL Database and open it to investigate the details.

**1 .**  Click on the **Databases** option on the top menu.

- In the list of datbases, you should see the database named like **&lt;your_lab_user_name&gt;-AD-Fin-PreMod**

**2 .**  Double-click on the database name to drill into main dashboard for the database.

![image](/images/mobilize/database_01.png)

## Database Overview

The native MySQL database used in the pre-modern version of the application is straining to keep up with the demand of the application load.  Let's take a look at the details of how the MySQL database is performing.


**1 .**  Click on the colored health status circle to see details of the server health

**2 .**  Observe the total time spent executing SQL statements during the specified time period

**2 .**  Observe the total number of executions during the specified time period

**4 .**  Hover over the time series on the chart to see the detail of the recorded metrics

**5 .**  Hover over the labels for each wait state to see a more detailed description

You can read more about the Database Overview dashboard <a href="https://docs.appdynamics.com/display/latest/Database+Dashboard" target="_blank">**here**</a>

![image](/images/mobilize/database_02.png)


## Activity Reports

There are up to nine different reports available in Database Visibility on the Database Activity Window. The reports available depend on the database platform being monitored. Let's investigate the Wait State Report to see which wait states are consuming the most time.

This report displays time-series data on Wait Events (states) within the database. Each distinct wait is color-coded, and the Y-axis displays time in seconds. This report also displays data in a table and highlights the time spent in each wait state.

The wait states consuming the most time may point to performance bottlenecks. For example, db file sequential reads may be caused by segment header contention on indexes or by disk contention.

You can read more about the Database Activity Reports <a href="https://docs.appdynamics.com/display/latest/Database+Activity+Window" target="_blank">**here**</a>

![image](/images/mobilize/database_03.png)


## Queries Summary Dashboard

The Queries window displays the SQL statements and stored procedures that consume the most time in the database. You can compare the query weights to other metrics such as SQL wait times to determine SQL that requires tuning.  From this view we can see **in this example, the select query related to audit data reporting has a 50% database resource usage rating** compared to all the other queries being executed.

**1 .**  Click on the "Queries" tab to view the queries window

**2 .**  Click on the "Top Queries" dropdown to display the top 5, 10, 100 or 200 queries

**3 .**  Click "Filter by Wait States" button to choose wait states to filter the Query list by

**4 .**  Click on the query that shows the largest "Weight (%)" used

**5 .**  Click on the "View Query Details" button to drill into the query details

You can read more about the Database Queries dashboard <a href="https://docs.appdynamics.com/display/latest/Database+Queries+Window" target="_blank">**here**</a>

![image](/images/mobilize/database_04.png)


## Query Detail View

Once you have identified the statements on the Database Queries window that are spending the most amount of time in the database, you can dig down deeper for details that can help you tune those SQL statements. The database instance Query Details window displays details about the query selected on the Database Queries window.

**1 .**  Resource consumption over time shows the amount of time the query spent in the database using resources, the number of executions, and the amount of CPU time consumed.

**2 .**  Wait states are the activities that contribute to the time it takes the database to service the selected SQL statement. The wait states consuming the most time may point to performance bottlenecks.

**3 .**  Click on the **Execution Plan** option to see the query execution plan window.

You can read more about the Database Query Details dashboard <a href="https://docs.appdynamics.com/display/latest/Database+Query+Details+Window" target="_blank">**here**</a>

![image](/images/mobilize/database_05.png)


## Troublshoot the Expensive Audit Query

The Database Query Execution Plan window can help you to determine the most efficient execution plan for your queries. Once you've discovered a potentially problematic query, you can run the EXPLAIN PLAN statement to check the execution plan that the database created. A query's execution plan reveals whether the query is optimizing its use of indexes and executing efficiently. This information is useful for troubleshooting queries that are executing slowly.

**1 .**  Notice that the join type in the "Type" column is ALL for each table.

**2 .**  Hover over one of the join types to see the description for the join type.
- The description points to the use of full table scans across the two tables in the query

**3 .**  Examine the entries in the "Extra" column.

**4 .**  Hover over each of the entries to see the description for the entry.

**5 .**  Click on the **Explain** button if you're not seeing the explain plan.

You can read more about the Database Query Execution Plan view <a href="https://docs.appdynamics.com/display/latest/Database+Query+Execution+Plan+Window" target="_blank">**here**</a>

![image](/images/mobilize/database_06.png)



## Here's the Advantage

- **Easily troubleshoot database problems** such as **slow response times and excessive load**
- Get immediate **insight into SQL statements or stored procedures** that are **consuming most of the DB resources**
- Easily **confirm time spent** on **fetching, sorting, or waiting on a lock**

{{% notice info %}}
All the dashboards seen in this section are provided OOTB and the content they contain is real-time, dynamic, and reflects the data gathered from the AppDynamics Database Monitoring Agent.
{{% /notice %}}

## Takeaways

- We **quickly identified** the **problematic query associated with audit reporting**
- We confirmed that **audit data reporting queries** are **consuming most of the DB resources**
- We **validated** the **need to separate** the **audit data from transactional loan approval data**

## Next <i class='fas fa-cog fa-spin'></i>

Let's **review** what we've learned about **how AppDynamics can accelerate** your efforts during **the Mobilize phase**.

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
