# 6. Overview: RHPAM Installation on OpenShift

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

For example, if you want an environment to author rules and processes, you can use the `rhpam79-authoring` that contains all the components necessary to do so. See the image below.

![RHPAM 70 Authoring]({% image_path rhpam-authoring.png %}){:width="600px"}

For this workshop, the authoring template would be enough to provide a complete authoring environment with a process server for you to test your assets. However due to the restrictions of the infrastructure of this environment (the platform does not provide persistent storage), the installation was made based on the ephemeral template instead.

![RHPAM 70 Ephemeral]({% image_path rhpam-ephemeral-template.png %}){:width="600px"}