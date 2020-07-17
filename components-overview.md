# RHPAM Components and Architecture

Red Hat Process Automation Manager enables you to automate different pieces of your business requirements like automating the decision making, the flow of the decision making, the interaction between the people and systems, etc.

The following diagram depicts the main capabilities of Red Hat Process Automation Platform (RHPAM).

![High Level Capability Component]({% image_path high-level-capability-components.png %}){:width="600px"}

## Capabilities Overview

### Decision Management
RHPAM includes all the benefits of Red Hat Decision Manager, therefore, it contains a high-performant, lightweight and scalable rules execution engine based on the open-source [Drools](http://www.drools.org) community project. This being said, PAM allows:

- Automating rules using decision tables, guided rules, drools, and the DMN (Decision Model and Notation) standard;
- Using PMML models as business assets, allowing the usage of AI/ML models within decision making and business flows;
- Usage of test scenario to validate the rules;
- Complex Event Processing, decision made on top of time-based events (i.e. fraud detection);

### Business Optimizer
An AI Constraint Satisfaction Solver that optimizes business resource planning use cases such as vehicle routing, employee rostering and conference scheduling. The platform optimizes the goal of a problem based on limited resources under specific constraints. The engine is based on the upstream [OptaPlanner](http://www.optaplanner.org) project.

### Process Management
A high-performant, lightweight and scalable, BPMN2 compliant, process execution engine based on the open-source [jBPM](http://www.jbpm.org) project. Provides functionality like business process management, case management and human task management, to enable the automation and optimization of processes and cases.

### Application management
A modern workbench that provides user the tooling to build business automation projects consisting of processes, rules, cases, and forms. Also, the workbench provides the management and monitoring functionality to build, deploy, run, manage and monitor business automation and process driven applications.

---

## Architectural components

In order to be able to correctly install and provision an RHPAM environment, you should first get familiar with the platform components. With the available components in mind you can understand the different possible ways to configure the product and be able to support different use cases.

On this Workshop, we are considering OCP as the installation platform. The OpenShift self-service console will allow you to provision, recreate, destroy your working environment and be autonomous from other users.

Red Hat PAM main components and capabilities are displayed in this diagram:

![RHPAM 7 Componens]({% image_path rhpam-components.png %}){:width="600px"}

### Business Central Monitoring
A modern web-based workbench that provides user the tooling to manage and monitor deployed projects, running engines, running instances of process-driven applications and more.

### Business Central Authoring
A web-based workbench used to manage business projects as well as providing powerful tools to build and author the business assets available in RHPAM, like different types of rules, processes, cases, test scenarios, data objects, etc.

### Asset Repository
Based on a collaborative line-of-thought, all of the assets developed using Business Central are stored in a git-based asset repository. This allows you to version, index, search and share your work with the rest of your team.

### Artifact Repository
Once you have completed the authoring phase and you are satisfied with the work, you can package your assets into a _Deployment Unit_ known as a _kjar_. This unit is a standard Java Archive (JAR) and will be stored in the artifact repository (i.e. Nexus, etc... ).

### Controller
The deployment units are deployed to the Execution Engine by the Controller. The Controller abstracts the complexity of the runtime environment through the use of so called _Templates_, or _Server Configurations_. This greatly reduces the complexity of managing clustered and/or heterogeneous topologies, for example topologies in which Execution Engines are deployed and managed per line of business.

### KIE Server (Intelligent Process Server)
The lightweight, cloud-native, execution engine that runs the rules and processes contained in the deployment unit. KIE-Servers can be scaled horizontally and/or vertically in an automated fashion using the cloud native capabilities of OpenShift Container Platform. Since the state of the processes is stored in a persistent store (by default a relational database) you can consider the KIE-Servers to be stateless when it comes to process execution.

### Smart Router
Provides a runtime abstraction layer over the KIE-Server topology, allowing clients of this topology to interact with a single endpoint. Smart Router contains the information of which processes and rules (deployment units) are deployed on which runtime engine/KIE-Server, and provides routing functionality to the correct server instance based on the client request. In a classical enterprise environment where you have multiple instances running and different nodes, starting and shutting down in an elastic way, the complexity of tracking these changes in order to correctly load-balance the requests is the responsibility of the Smart Router.

## PAM architecture

RHPAM can be architected in some different ways, this is a represention of one of the possible architectures:

![RHPAM 7 Architecture]({% image_path rhpam-7-architecture.png %}){:width="600px"}

----

**About the environment in this Workshop**

Because a critical capability of a digitally enabled product is to be available as a service, we are going to leverage  OpenShift Container Platform as a self-service console where you can choose the different tools needed depending on your skills, LOB and solution. Let's see how PAM behaves within OpenShift.
