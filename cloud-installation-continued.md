# Installing RHPAM via Template

In this lab, we are going to create a new project and provision a whole environment using the RHPAM Trial Ephemeral.

1. If you are not already logged in into the OpenShift Web Console, open it on using the tab on the upper right side of your screen. Login with username `userX` {{copy}} and password `openshift`{{copy}};
2. On the left menu, select the `Developer` perspective.

![Installation Select Developer Perspective]({% image_path developer-perspective-menu.png %}){:width="600px"}

3. Click on `Project: rhpam-userX`, and select `Create Project`. Use the following values for your project
  - Name: `credit-card-dispute`{{copy}}
  - Display Name: `Credit Card Dispute`{{copy}}
  - Description: `Red Hat Process Automation Manager 7 Credit Card Dispute demo`{{copy}}

![Installation Create Project]({% image_path create-project.png %}){:width="600px"}

4. The _Topology_ window will be displayed. We will provision a new RHPAM environment from the OpenShift catalog. Click on the option `From Catalog`, and search for `Red Hat Process Automation Manager 7.5 ephemeral trial environment` title.

![Installation Select Template]({% image_path installation-select-template.png %}){:width="600px"}

5. Click on the blue button `Instantiate Template`;

4. In the form that opens, fill-in the following values:
  - Application Name: `cc-dispute`{{copy}}
  - Default Password: `developer`{{copy}}
  - KIE Admin User: `developer`{{copy}}
  - KIE Server User: `developer`{{copy}}

![Installation Template Form]({% image_path installation-template-form.png %}){:width="600px"}

5. Scroll down to the bottom of the form and click on the `Create` button. You should be automatically redirected to the `Template Instance Details`. All the details of what is happening, on the left menu you can click on `Events` and observe OpenShift processing the template and provisioning all the objects of the new environment. _It's common to see probe failing for a couple of minutes while the services are booting. Feel free to watch the logs and details of pods individually to confirm the services are booting_.

6. To check the final status, on the left menu go to  under `Advanced`, select `Projects` and click on the `credit-card-dispute` project. Finally, click on `Workloads` tab.

6. When the provisioning is complete, the workloads page should show a `cc-dispute-kieserver` deployment and `cc-dispute-rhpamcentr` deployment. The first represents the execution server, the latter the _Business Central_ workbench.

![Installation Provisioned]({% image_path installation-provisioned.png %}){:width="600px"}

Congratulations, you just provisioned an RHPAM environment on OpenShift 4! On the next step, let's validate the installation and test the environment.
