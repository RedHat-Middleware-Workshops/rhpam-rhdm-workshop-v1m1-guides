#  Business Central Security

So far you received access to the OpenShift where your PAM environment is available. Now we will access PAM workbench known as Business Central.

Business Central has authoring, management and monitoring capabilities both for developers as well as subject domain experts.

![Collaboration Tools]({% image_path collaboration_tools.png %}){:width="600px"}

Let's start by accessing your business central.

## Accessing Business Central

_Jump to step 2 if you're already logged into OpenShift._

1. [Go to your Openshift console](https://{{ OPENSHIFT_CONSOLE_URL }}){:target="_blank"} tab.  If you're not yet logged in, or have been logged out, login using the same credentials as before:

- user: `userX`{{copy}}
- password: `openshift`{{copy}}

![OpenShift Console]({% image_path openshift-console.png %}){:width="600px"}

2. Make sure you are on the `Developer` perspective. On the left menu, select the `Topology` option and check if you have the `rhpam-userX` project selected. .

3. You will see listed the 3 components: `rhpam7-rhpamcentr`, the `rhpam7-kieserver` and `react-web-app`.
At this point we are interested on the authoring environment. From this page, you can already find a link to open Business Central:

![PAM Project]({% image_path topology-details.png %}){:width="600px"}

4. Click on the link for `rhpam7-rhpamcentr` (4 Step on image above). That link is the external OpenShift route that allows us to access Business Central. A new tab should open with Business Central login page.

5. You can login in Business Central with the following credentials:

 - user: `pamAdmin`{{copy}}
 - password: `redhatpam1!`{{copy}}

![Business Central Console]({% image_path business-central-console.png %}){:width="600px"}

If you can see the page above, this means you could access the working environment where users can author and test their Business Applications.

Let's head over to have an overview about how user authentication and authorization works within Business Central.
