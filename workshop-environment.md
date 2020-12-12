# 4. Accessing your work environment

The cloud native OpenShift environment has already been provisioned for you. You can access it either via a terminal command line (for example if you're an IT professional) or via a web-based console. In this Workshop you will have your own OpenShift namespace to work.

## Environment Details

1. This is the link to access [Red Hat Openshift Container Platform]({{ OPENSHIFT_CONSOLE_URL }}){:target="_blank"}
2. The instructor should also assign to you a unique user number, which you will use from now on to access your OCP environment.
    - OpenShift Console username: userX (i.e. user1)
    - OpenShift Console password: openshift

## Login on OpenShift

In this workshop, you can choose between two possible ways to interact with OpenShift: Web Console or Command Line.

### Via Web Console

To access OpenShift via the Web Console:

1. Open the [Red Hat Openshift Container Platform]({{ OPENSHIFT_CONSOLE_URL }}) in your browser.
2. Login with username `userX`{{copy}} and password `openshift`{{copy}}
3. You will see a list of the projects that you have access to. In this case, only the _rhpam-userX_ project.
4. Finally, click on the project to open the project page.

### Via Command Line

In order to login via CLI, you will need in your local environment the OpenShift CLI tool. If you don't have it, you can select and download the [OpenShift CLI tool](https://mirror.openshift.com/pub/openshift-v4/clients/ocp/4.2.25/openshift-client-linux-4.2.25.tar.gz) according to your environment.

Alternatively, you can use a browser based OpenShift terminal. Your instructors will show this option if need it.

The easiest way to login to the OpenShift system via the command line interface, is to access it via Web Console, log in and click on `Copy Login Command`.

![OCP Copy Login Command]({% image_path ocp-copy-login-command.png %}){:width="600px"}

1. Login to [Openshift Console]({{ OPENSHIFT_CONSOLE_URL }}){:target="_blank"}
2. Click on `Copy Login Command`
3. OpenShift will request your credentials again. Inform them.
4. Click on `Display Token`
5. Look for the `Login with this token` session, and copy the command which is similar to:

```
oc login --token=rVO1oDOjspF6CLTW53zddinWRrpxAfDsywzptM0jsiY --server=https://api.cluster-rio-ead1.rio-ead1.example.opentlc.com:6443
```

We have already provisioned an environment for you, and a project called **_rhpam-userX_**.

## Red Hat Process Automation Manager on OpenShift Platform

Once you are in the platform, on the left menu you can find the `Home` section, and under it, you shoud click on `Projects`. Select the project `rhpam-userX`, and click on the `Workloads` tab. You can see there are two applications:

  - `react-web-app`: A react application which communicates via REST and consumes business assets from PAM engine (Kie Server);

  - `rhpam78-authoring`: An environment that allows authoring, execution and monitoring of business assets; 

  ![RHPAM Operator]({% image_path rhpam-projects.png %}){:width="600px"}

Inside these application you can see three pods listed:

  - `react-web-app`
    - `react-web-app`: Pod containing the react client application;
  - `rhpam78-authoring`
    - `rhpam7-kieserver`: Pod containing PAM execution engine (Kie Server);
    - `rhpam7-rhpamcentr`: Por containing Business Central, for authoring, management and monitoring;

As you can notice, when deployed on OCP, each component of Red Hat PAM is provisioned within it's own pod. The components above and environment are the ones which we are going to use during this workshop.

<!-- ### Provisioning PAM from scratch

The Workloads page shows the  current working environment provisioned for you. But what if you have special needs of tools and components? Or you simply want to know what you are working on.

Let's go ahead and create a whole new project using Red Hat PAM Templates and starting a new deployment based on your requirements.

RHPAM 7.5 brings with it an OpenShift operator that can simplify the installation process. The operator creates for the deployed environment an YAML, and based on it, it ensures that the environment remains consistent in all times.  
 -->
<!---
#### RHPAM Operator

 Since Red Hat PAM 7.5, Red Hat PAM brings OpenShift Operators to help on easily deploying new instances. Let's use the provided operator to create a new environment.

 [#TODO] will require pre-provisioning the operator in each user namespace;

//// -->

Now that we know more details about the environment where PAM is running, let's access it!
