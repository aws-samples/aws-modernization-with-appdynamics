+++
title = "Deployment"
chapter = false
weight = 1
hidden = true
+++

![image](/images/operate/ad_team_cloudops.png)


## Deploy the Cluster Agent to EKS

It's time to deploy the Cluster Agent to the EKS cluster.  Let's start by looking at the script that deploys the Cluster Agent to the cluster using the commands below in your Cloud9 terminal:

```
cd /opt/appdynamics/workshopuser

cat -n deployClusterAgent.sh
```

The script is performing the following actions:
 - Changing to the directory where the agent YAML files reside
 - Creates a namespace for the agent
 - Deploys the Cluster Agent Operator
 - Creates the Access Key for the agent
 - Deploys the Cluster Agent
 - Deploys the Kubernetes Metric Server

The script uses <a href="https://kubernetes.io/docs/reference/kubectl/overview/" target="_blank">**kubectl**</a> to perform the deployment.

Take a quick look at the **cluster-agent.yaml** file using the commands below:

```
cd /opt/appdynamics/workshopuser/post-mod-kube-ca

cat -n cluster-agent.yaml
```

![image](/images/operate/kube-config-01.png)

The setup script you executed in the workshop setup section, auto-populated the agent to controller configuration properties for you.

**How does** the Cluster Agent know how to connect to the controller **?**
 - on **line 8 - 9** we are providing the controller URL and the account name

**Where do we** reference the Docker image of the Cluster Agent **?**
 - on **line 11** we are providing the reference to the pre-built public image that can be found <a href="https://hub.docker.com/r/appdynamics/cluster-agent/tags?page=1&ordering=last_updated" target="_blank">**here**</a>


You can proceed to deploy the Cluster Agent using the commands below:

```
cd /opt/appdynamics/workshopuser

./deployClusterAgent.sh
```

The image below shows what the output looks like for Cluster Agent deployment.

![image](/images/operate/kube-deploy-01.png)


You can read more about deploying the Cluster Agent <a href="https://docs.appdynamics.com/appd/23.x/latest/en/infrastructure-visibility/monitor-kubernetes-with-the-cluster-agent/install-the-cluster-agent" target="_blank">**here**</a>


## Next <i class='fas fa-cog fa-spin'></i>

In the next section we'll look at how you can **unlock the power of machine learning and AI** to deliver world-class user experience **with AppDynamics Cognition Engine**.



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



