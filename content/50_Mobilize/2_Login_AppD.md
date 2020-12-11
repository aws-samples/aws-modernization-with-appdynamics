+++
title = "Login to AppDynamics"
chapter = false
weight = 2
+++

![image](/images/mobilize/ad_team_architect.png)


## Login to the AppDynamics Controller

Once the setup utility has finished, you can find your login credentials to your AppDynamics Controller by using the commands below:

```
cd /home/ec2-user/environment

cat workshop-user-details.txt
```

Your workshop user details file should have the following information similar to the image below:

- The URL to the AppDynamics Controller you will use
- The credentials you will use to login to the Controller
- The names of the Pre-Modernization APM and EUM applications
- The names of the Post-Modernization APM and EUM applications

![image](/images/mobilize/user_details.png)

In a separate browser tab or window, navigate to the URL that is next to Controller URL in the workshop user details file. Use the data from the workshop user details file to login to AppDynamics.

{{% notice tip %}}
The account and username are two distinct fields that are used as part of logging in.
{{% /notice %}}

![image](/images/mobilize/appd_login.png)


## Next <i class='fas fa-cog fa-spin'></i>

 We'll start the **assessment of the pre-modernized version** of the **AD Financial web front-end**.


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



