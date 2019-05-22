# Security and configuration

Enterprise applications require enterprise class security implementations. At the same time, the security system, the system in which you define users, roles, groups and their respective authentication and authorization configurations, needs to be easy accessible and easy to use.

Red Hat Process Automation Manager provides a comprehensive security system, that's easy to configure and use. By default, the security system uses the local filesystem to store it's configuration, but, being an enterprise solution, can easily be configured to connect to, for an example, an enterprise LDAP system.

Second, Red Hat Process Automation Manager comes with the Red Hat Single Sign-On (RH SSO) platform, which enables you to secure your web applications by providing Web single sign-on (SSO) capabilities based on popular standards such as SAML 2.0, OpenID Connect and OAuth 2.0. This allows you to, among other things, secure the Red Hat Process Automation Manager web consoles, the REST endpoints to interact with the platform and the access to Git.

In this scenario we will learn how to use the out-of-the-box security management system of Red Hat Process Automation Manager to create new users and groups, which we need to implement our use-case.

In RHPAM, you have 2 different types of users:
- platform users: these are the users that interact with the authoring environment, for example the `developer` user that you used to log into the platform
- application users: these are the users that will interact with the process driven application that you're building with, and running on, the platform. In the case of our _Credit Card Dispute_ system, we have identified 3 different roles that will interact with the process:

![CCD Work Users]({% image_path ccd-workshop-users.png %}){:width="600px"}

In fact, we can see these are not individual users, but groups that the different user can belong to. Our bank has these 3 groups defined, and the tasks for each group will be defined and configured as you automate the process.

## User Configuration

1. RHPAM's workbench uses and activity-centered design approach, in which functionality is grouped according to the tasks that a user can (or must) perform. The functionality to administer users and groups can be found in the _Settings_ menu, which can be accessed by clicking on the _gear_ icon ![Gear Icon]({% image_path gear-icon.png %}){:width="600px"} in the upper right of the screen next to the questionmark icon.

![Engine Settings Menu]({% image_path engine-settings-menu.png %}){:width="600px"}

2. The _Settings_ menu shows all components that you can configure in your environment. In this step we will focus on the users and groups.

![Settings Menu]({% image_path settings-menu.png %}){:width="600px"}

3. Click the groups icon and you'll see the group administration menu, where you can list the groups that currently exist, update or delete them or create a new group.

![Groups Menu]({% image_path groups-menu.png %}){:width="600px"}

4. Click on `New Group`. We will add the following new groups:
  - `card-holder`{{copy}}
  - `agent`{{copy}}
  - `agent-manager`{{copy}}

After you type in the name of the group, in this case `card-holder`{{copy}} select the `adminUser` and click on `Add selected users` to add it to the `card-holder` group. In a real world scenario all these groups will be associated with different personas but for the sake of simplicity, your user will be part of all the groups needed, in order for you to be able to test the processes and application.

5. Repeat for the group `agent`{{copy}} and `agent-manager`{{copy}}.

![User Groups Settings Menu]({% image_path user-groups-settings-menu.png %}){:width="600px"}


***You have successfully completed the installation of your environment.***
