+++
title = "Create Cloud9 Workspace"
chapter = false
weight = 1
+++

![image](/images/workshop_setup/ad_team_tech_lead.png)

{{% notice warning %}}
The Cloud9 workspace should be built by an IAM user with Administrator privileges,
not the root account user. Please ensure you are logged in as an IAM user, not the root
account user.
{{% /notice %}}

<!---
{{% notice info %}}
This workshop was designed to run in the **Oregon (us-west-2)** region. **Please don't
run in any other region.** Future versions of this workshop will expand region availability,
and this message will be removed.
{{% /notice %}}
-->

{{% notice tip %}}
Ad blockers, javascript disablers, and tracking blockers should be disabled for
the cloud9 domain, or connecting to the workspace might be impacted.
Cloud9 requires third-party-cookies. You can whitelist the <a href="https://docs.aws.amazon.com/cloud9/latest/user-guide/troubleshooting.html#troubleshooting-env-loading" target="_blank">**specific domains**</a>.
{{% /notice %}}


## Launch Cloud9 in your closest region

Use a single region for the duration of this workshop. This workshop supports the following regions, however:

{{% notice info %}}
If you are using the **Events Engine please be aware** that there are **only two regions suported**. They are **N. California - us-west-1** and **Oregon - us-west-2**
{{% /notice %}}

- **N. California** 
  - <a href="https://us-west-1.console.aws.amazon.com/cloud9/home?region=us-west-1" target="_blank">**N. California - us-west-1**</a> 
  
- **Oregon** 
  - <a href="https://us-west-2.console.aws.amazon.com/cloud9/home?region=us-west-2" target="_blank">**Oregon - us-west-2**</a>

- **N. Virginia** 
  - <a href="https://us-east-1.console.aws.amazon.com/cloud9/home?region=us-east-1" target="_blank">**N. Virginia - us-east-1**</a>

- **Ohio** 
  - <a href="https://us-east-2.console.aws.amazon.com/cloud9/home?region=us-east-2" target="_blank">**Ohio - us-east-2**</a>

- **Ireland** 
  - <a href="https://eu-west-1.console.aws.amazon.com/cloud9/home?region=eu-west-1" target="_blank">**Ireland - eu-west-1**</a>

- **Singapore** 
  - <a href="https://ap-southeast-1.console.aws.amazon.com/cloud9/home?region=ap-southeast-1" target="_blank">**Singapore - ap-southeast-1**</a>


{{% notice warning %}}
You **must use** the **t3.large** instance type for this workshop.  If the **t3.large** instance type is not available in the region you first selected, please choose a different region where the **t3.large** instance type is available.
{{% /notice %}}

{{% notice warning %}}
You **must use** the **Amazon Linux 2** platform type for this workshop.  If the **Amazon Linux 2** platform type is not available in the region you first selected, please choose a different region where the **Amazon Linux 2** platform type is available.
{{% /notice %}}

## Select your options

- Select **Create environment**
- Name it **AppDynamics-Workshop**, click Next.
- Choose **t3.large** for instance type, ensure **Amazon Linux 2** is selcted as the platform, choose **After four hours** for cost saving setting, as seen below.


![c9configure](/images/workshop_setup/c9_configure_01.png)

- Click **Next Step**, then click **Create environment**
  
- When it comes up, customize the environment by closing the **welcome tab**
and **lower work area**, and opening a new **terminal** tab in the main work area:
![c9before](/images/workshop_setup/c9_before.png)

- Your workspace should now look like this:
![c9after](/images/workshop_setup/c9_after.png)

- If you like this theme, you can choose it yourself by selecting **View / Themes / Solarized / Solarized Dark**
in the Cloud9 workspace menu.