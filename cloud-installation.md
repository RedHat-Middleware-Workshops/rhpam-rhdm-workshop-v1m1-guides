# Setting up the work environment

Red Hat Process Automation Manager is part of a rich set of tools to develop enterprise solution thought to support multidisciplinary teams with the right tools for the tasks at hand.

The cloud native OpenShift environment has already been provisioned for you. You can access it either via a terminal command line (for example if you're an IT professional) or via a web-based console. In this Workshop you will have your own Openshift namespace to work.

## Environment Details

1. The instructor should inform you the URL of Openshift environment where you can access the labs environment;
I.e. `https://console-openshift-console.apps.cluster-rio-ead1.rio-ead1.example.opentlc.com/`
2. The instructor should also assign to you a unique user number, which you will use from now on to access your OCP environment.
  - Openshift Console username: userX (i.e. user1)
  - Openshift Console password: openshift

## Login on Openshift

In this workshop, you can choose between two possible ways to interact with Openshift: Web Console or Command Line.

### Web Console

You can interact with the OpenShift Container Platform via the Web Console.

- Open the Openshift console in your browser using the URL provided.
- Login with username `userX`{{copy}} and password `openshift`{{copy}}
- You will see a list of the projects that you have access to. In this case this is only the _rhpam-userX_ project. Click on the project to open the project page.

### Command Line

The easiest way to login to the OpenShift system via the command line interface, is to access it via Web Console, login and click on `Copy Login Command`.

![OCP Copy Login Command]({% image_path ocp-copy-login-command.png %}){:width="600px"}

- Login to Openshift Web Console
- Click on `Copy Login Command`
- Openshift will request your credentials again. Inform them.
- Click on `Display Token`
- Look for the `Login with this token` session, and copy the command which is similar to:

```
oc login --token=rVO1oDOjspF6CLTW53zddinWRrpxAfDsywzptM0jsiY --server=https://api.cluster-rio-ead1.rio-ead1.example.opentlc.com:6443
```

As you can see, the IT engineers have already provisioned an environment for you in a project called _rhpam-userX_.

## Red Hat Process Automation Platform on Openshift

After clicking on the project, select the `Workloads` tab. You can see there are two applications:
- `react-web-app`: A react application which communicates via REST and consumes business assets from PAM engine (Kie Server);
- `rhpam75-trial-ephemeral`: An environment that allows authoring, execution and monitoring of business assets; _This is an ephemeral environment, in other words, it does not have persistent storage._

Inside these application you can see three pods listed within the two applications
- `react-web-app`
  - `react-web-app`: Pod containing the react client application;
- `rhpam75-trial-ephemeral`
  - `rhpam7-kieserver`: Pod containing PAM execution engine (Kie Server);
  - `rhpam7-rhpamcentr`: Por containing Business Central, for authoring, management and monitoring;

As you can nootice, when deployed on OCP, each component of Red Hat PAM is provisioned within it's own pod.

### Provisioning PAM from scratch

The Workloads page shows the  current working environment provisioned for you. But what if you have special needs of tools and components? Or you simply want to know what you are working on.

Let's go ahead and create a whole new project using Red Hat PAM Templates and starting a new deployment based on your requirements.

RHPAM 7.5 brings with it an Openshift operator that can simplify the installation process. The operator creates for the deployed environment an YAML, and based on it, it ensures that the environment remains consistent in all times.  

<!---
#### RHPAM Operator

 Since Red Hat PAM 7.5, Red Hat PAM brings Openshift Operators to help on easily deploying new instances. Let's use the provided operator to create a new environment.

 [#TODO] will require pre-provisioning the operator in each user namespace;

//// -->

#### Templates

What is an installation template? Red Hat Process Automation Manager's design is activity focused. This means that you have predefined environments available for you to deploy depending on what you want to accomplish. The definitions are modeled in the form of templates. A template describes an environment that follows a Red Hat prescriptive deployment architecture. Templates are provided that define and deploys a fully working platform for development, test, production, etc. Depending on whether you want to develop, integrate, test or run processes and other assets, you can choose your environment of choice.

Some examples of the available templates are:

- `rhpam75-authoring`: The environment of choice if you are a business user or developer that wants to author business automation projects, assets and applications. Provides an authoring environment including the workbench and an execution server.
- `rhpam75-authoring-ha`: Same as the previous environment, but with high availability features. This implies that there are multiple (by default 2) instances of Business Central and execution server deployed.
- `rhpam75-trial-ephemeral`: If you want a quick demo environment to test the platform. Provides the same environment as the `authoring` template but without persistent storage.
- `rhpam75-prod`: If you are the administrator of the platform and you want a production like environment. The template provisions a monitoring and management environment, a smart router and 2 execution server groups.

What kind of environment is right for your you depends on your requirements:
- In which deployment environment is the platform going to be provisioned?
  - Is the environment planned for process and/or rules development?
  - Is the environment planned for integration testing?
  - Is the environment planned to be a production environment?
- What kind of deployment architecture and methodology do you prefer?
  - Do you want to be able to install and update process definitions and rules via the management console?
  - Do you use the concept of immutable containers, and thus don't allow the provisioning of applications through the management console?
- Do you have a requirement for high availability of the platform?
- What kind of database do you want to integrate with?

For example, if you want an environment to author rules and processes, you can use the `rhpam75-authoring.yaml` that contains all the components necessary to do so. See the image below.

<!--- #TODO Update image -->
![RHPAM 70 Authoring]({% image_path rhpam70-authoring.png %}){:width="600px"}

-----------

Quiz: From the previous step, what components do you recognize in this template?

-----------
In the case of this workshop, because you need a complete authoring environment with a process server where you can test your assets, we could (or should) deploy the authoring environment. However due to the restrictions of this environment (the platform does not provide persistent storage), we will use the ephemeral template instead.

<!--- #TODO Update image -->
![RHPAM 70 Ephemeral]({% image_path rhpam70-ephemeral-template.png %}){:width="600px"}
