# Security in PAM

Red Hat Process Automation Manager security system is based on users, roles and groups. These configurations comes by default from the application server PAM is running on top of, in this case Red Hat Enterprise Application Server (Red Hat EAP).  

When working in an enterprise architecture, it is recommended to connect RHPAM to an external provider like an enterprise LDAP system or an identity provider like Red Hat Single Sign On (a.k.a. Keycloak).

In this lab, we will learn how to use the out-of-the-box security management system of Red Hat Process Automation Manager to create new users and groups, which we need to implement our use-case.

In RHPAM, you have 2 different types of users:
- **platform users**: these are the users that interact with Business Central, the authoring environment, for example the `pamAdmin` user that you used to log in to the workbench;
- **application users**: these are the users that will interact with the process driven application that you're building with, and running on, the platform. In the case of our _Credit Card Dispute_ system, we have identified 3 different roles that will interact with the process: the **CC Holder**, the **Manager** and the **Agent** groups who works in Pecunia Corp.

![CCD Work Users]({% image_path ccd-workshop-users.png %}){:width="600px"}

In fact, we can see these are not individual users, but groups that the different user can belong to. Our bank has these 3 groups defined, and the tasks for each group will be defined and configured as you automate the process.

## User Configuration in Business Central

Business Central uses and activity-centered design approach, in which functionality is grouped according to the tasks that a user can (or must) perform.

1. To access the functionality to administer users and groups, select the _Settings_ menu, the _gear_ icon ![Gear Icon]({% image_path gear-icon.png %}){:width="600px"} in the upper right of the screen.

![Engine Settings Menu]({% image_path engine-settings-menu.png %}){:width="600px"}

2. The _Settings_ menu shows all components that you can configure in your environment. In this step we will focus on the users and groups.

![Settings Menu]({% image_path settings-menu.png %}){:width="600px"}

3. Click the `Groups` option and you'll see the group administration menu, where you can list the groups that currently exist, update or delete them or create a new group.

![Groups Menu]({% image_path groups-menu.png %}){:width="600px"}

4. Click on `New Group`. The name group is `card-holder`{{copy}}. 5. After you type in the name of the group, in this case `card-holder`{{copy}}, select the `pamAdmin` and click on `Add selected users` to add it to the `card-holder` group.

_In a real world scenario all these groups will be associated with different personas but for the sake of simplicity, your user will be part of all the groups needed, in order for you to be able to test the processes and application._

5. Repeat for the groups `agent`{{copy}} and `agent-manager`{{copy}}.

At the end you should have three groups:
- `card-holder`{{copy}}
- `agent`{{copy}}
- `agent-manager`{{copy}}

![User Groups Settings Menu]({% image_path user-groups-settings-menu.png %}){:width="600px"}  

**You have successfully completed the groups configuration of your environment.**
