+++
title = "AD Financial Web UI"
chapter = false
weight = 1
hidden = true
+++

![image](/images/mobilize/ad_team_architect.png)

 

## AD Financial on the Web

Before we login to the AppDynamics console to observe the pre-modernized version of the application, let's take a quick look at the web interface of the application from an end users perspective. 

Use the following steps to find the URL to the web site:

**1 .**  Go to your Cloud9 console and click on the **Preview** option at the top

**2 .**  Then select **Preview Running Application** from the drop down

**3 .**  If the web home page doesn't show up, you may need to click in the address bar and add **:8080** after **amazonaws.com** at the end of the URL and hit enter

**4 .**  Now click on the button **to the right of the "Browser" button** to open the web page in a new browser tab

{{% notice info %}}
If the web page doesn't come up then try using a different browser. Chrome usually works the best.
{{% /notice %}}

![image](/images/mobilize/find_web_url_01.png)

<br>

## Login to the Web Site

Use the following steps to login to the web site:

**1 .**  Type in **batman** for the online id / user name

**2 .**  Type in any password of your choosing

**3 .**  Click on the **Sign In** button  to login

![image](/images/mobilize/web_site_01.png)


Now that you are logged in, you should see the different accounts for the user:

 - Personal Checking
 - Personal Savings
 - Auto Loan
 - Home Loan

![image](/images/mobilize/web_site_02.png)


Click on any of the four accounts to see the transaction history.  You can click on the **Accounts** tab on the top menu to navigate back to the accounts summary screen.


![image](/images/mobilize/web_site_03.png)


## Next <i class='fas fa-cog fa-spin'></i>

 We'll walk through the login process for the AppDynamics Controller that you'll be using throughout the workshop.


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



