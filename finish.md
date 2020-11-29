This scenario has explained the main components of RHPAM and provided you information on how the installation should be done over OpenShift. It also guided you on how to access and configure your environment to start authoring business assets.

In the next scenarios you will learn how to build those assets based on the use case described in this module.

### Environment information summarized

To access OpenShift via the Web Console:

1. Open the [Red Hat Openshift Container Platform]({{ OPENSHIFT_CONSOLE_URL }}) in your browser.
2. Login with username `userX`{{copy}} and password `openshift`{{copy}}
3. You will see a list of the projects that you have access to. In this case, only the _rhpam-userX_ project.
4. Finally, click on the project to open the project page.

To access Business Central: 

1. Login to your [Openshift console](https://{{ OPENSHIFT_CONSOLE_URL }}){:target="_blank"} tab.

2. Make sure you are on the `Developer` perspective. On the left menu, select the `Topology` option and check if you have the `rhpam-userX` project selected. .

3. To Business Central, click on the link for `rhpam7-rhpamcentr` (4 Step on image below):

	![PAM Project]({% image_path topology-details.png %}){:width="600px"}

5. Login in Business Central with the following credentials:

 - user: `pamAdmin`{{copy}}
 - password: `redhatpam1!`{{copy}}