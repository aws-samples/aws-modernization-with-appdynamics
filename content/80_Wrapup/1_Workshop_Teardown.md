+++
title = "Workshop Cleanup"
chapter = false
weight = 1
+++

<br>

#### Congratulations! &nbsp;&nbsp; You have successfully completed the Advanced Observability with AppDynamics workshop! &nbsp;&nbsp; 

#### Before we start the teardown process, please complete <a href="https://www.ciscofeedback.vovici.com/se/6A5348A77B63B6DC" target="_blank">**this survey**</a> and let us know how you liked the workshop. 

#### The feedback you provide will help us with improving this workshop along with future workshops.

<br>

{{% notice warning %}}
In order to prevent charges to your AWS account, we recommend cleaning up the infrastructure that was created. If you plan to keep things running so you can examine the workshop a bit more, please remember to do the cleanup when you are done. It is very easy to leave things running in an AWS account, forget about it, and then accrue charges.
{{% /notice %}}

<span style="color: #4e3eb1;"><i class='fas fa-circle fa-sm'></i></span> Execute the commands below to cleanup all workshop resources:

```
cd /home/ec2-user/environment

./teardownWorkshop.sh 
```

{{% notice info %}}
The setup utility takes approximately 10 minutes to complete.
{{% /notice %}}

<span style="color: #4e3eb1;"><i class='fas fa-circle fa-sm'></i></span> The output from the teardown script when it starts, should look like this:

![image](/images/wrapup/teardown_start.png)


<span style="color: #4e3eb1;"><i class='fas fa-circle fa-sm'></i></span> The output from the teardown script when it deletes the EKS cluster, should look like this:

![image](/images/wrapup/teardown_middle.png)


<span style="color: #4e3eb1;"><i class='fas fa-circle fa-sm'></i></span> The output from the teardown script when it ends, should look like this:

![image](/images/wrapup/teardown_end.png)

## Next <i class='fas fa-cog fa-spin'></i>

We'll walk through the **steps to cleanup the Cloud9 instance** you created for the workshop.
