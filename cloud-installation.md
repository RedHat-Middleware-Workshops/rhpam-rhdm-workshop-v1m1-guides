# Accessing your work environment

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

1. Login to [Openshift Console](https://{{ OPENSHIFT_CONSOLE_URL }}){:target="_blank"}
2. Click on `Copy Login Command`
3. OpenShift will request your credentials again. Inform them.
4. Click on `Display Token`
5. Look for the `Login with this token` session, and copy the command which is similar to:

```
oc login --token=rVO1oDOjspF6CLTW53zddinWRrpxAfDsywzptM0jsiY --server=https://api.cluster-rio-ead1.rio-ead1.example.opentlc.com:6443
```

We have already provisioned an environment for you, and a project called **_rhpam-userX_**.

## Red Hat Process Automation Manager on OpenShift Platform

Once you are in the platform, on the left menu you can find the `Home` section, and under it, you shoud click on `Projects`. You can see there are two applications:

  - `react-web-app`: A react application which communicates via REST and consumes business assets from PAM engine (Kie Server);

  - `rhpam75-trial-ephemeral`: An environment that allows authoring, execution and monitoring of business assets; _This is an ephemeral environment, in other words, it does not have persistent storage._

  ![RHPAM Operator]({% image_path rhpam-projects.png %}){:width="600px"}

Inside these application you can see three pods listed:

  - `react-web-app`
    - `react-web-app`: Pod containing the react client application;
  - `rhpam75-trial-ephemeral`
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

#### Overview: Installation on OpenShift

RHPAM installation on OpenShift can be made using an Operator or using pre-defined templates. This allows easy deployment of environments that aims specific goals.

_An Operator is a method of packaging, deploying and managing a Kubernetes application. A Kubernetes application is an application that is both deployed on Kubernetes and managed using the Kubernetes APIs and kubectl tooling._

So, depending on whether you want to develop, integrate, test or run processes and other assets, you can choose the installation configurations that will create an environment that reflects the needs of your choice. Once the architecture is defined, the user can opt to do the installation via template or using the RHPAM Operator available on the OperatorHub.

![RHPAM Operator]({% image_path rhpam-operator.png %}){:width="600px"}

When deploying PAM via Operator, the user will deploy a KieApp. It is possible to customize the configurations via yaml, or, use the Operation Installer UI provided by the operator:

![RHPAM Operator Installer UI]({% image_path rhpam-operator-installer-ui.png %}){:width="600px"}

Like mentioned, you have available some pre-defined templates to deploy PAM. Here are a summary some of the options:

- **rhpam-trial**: A trial environment that you can set up quickly and use to evaluate or demonstrate developing and running assets. Includes Business Central and a Process Server. This environment does not use any persistent storage, and any work you do in the environment is not saved.
- **rhpam-authoring**: The environment of choice if you are a business user or developer that wants to author business automation projects, assets and applications. Provides an authoring environment including Business Central and an execution server (Kie Server).
- **rhpam-authoring-ha**: Same as the previous environment, but with high availability features. This implies that there are multiple (by default 2) instances of Business Central and execution server deployed.
- **rhpam-production**: An environment for running existing services for staging and production purposes. If you are the administrator of the platform and you want a production like environment. The template provisions a monitoring and management environment, a smart router and 2 execution server groups.

<!-- What kind of environment is right for you, depends on your requirements:

- In which deployment environment is the platform going to be provisioned?
  - Is the environment planned for process and/or rules development?
  - Is the environment planned for integration testing?
  - Is the environment planned to be a production environment?
- What kind of deployment architecture and methodology do you prefer?
  - Do you want to be able to install and update process definitions and rules via the management console?
  - Do you use the concept of immutable containers, and thus don't allow the provisioning of applications through the management console?
- Do you have a requirement for high availability of the platform?
- What kind of database do you want to integrate with? -->

For example, if you want an environment to author rules and processes, you can use the `rhpam75-authoring` that contains all the components necessary to do so. See the image below.

![RHPAM 70 Authoring]({% image_path rhpam-authoring.png %}){:width="600px"}

For this workshop, the authoring template would be enough to provide a complete authoring environment with a process server for you to test your assets. However due to the restrictions of the infrastructure of this environment (the platform does not provide persistent storage), the installation was made based on the ephemeral template instead.

![RHPAM 70 Ephemeral]({% image_path rhpam-ephemeral-template.png %}){:width="600px"}

Now that we know more details about the environment where PAM is running, let's access it!
