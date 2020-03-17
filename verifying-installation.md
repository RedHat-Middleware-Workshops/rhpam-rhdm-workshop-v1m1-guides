# Verifying your installation

So far you received access to a working environment to author process and policies. Now we will verify the environment and the tools.

Business Central, a component of PAM, has authoring tools both for developers as well as subject domain experts.

![Collaboration Tools]({% image_path collaboration_tools.png %}){:width="600px"}

Let's start by accessing your business central.

## Business Central

1. Go to your OpenShift console tab. Go to step 2 if you're already logged in. If you're not yet logged in, or have been logged out, login using the same credentials as before:

- user: `userX`{{copy}}
- password: `openshift`{{copy}}

![OpenShift Console]({% image_path openshift-console.png %}){:width="600px"}

2. Make sure you are on the `Developer` perspective and that you have the `rhpam-userX` project selected. On the left menu, select the `Topology` option.

3. You will see listed the 3 components: `rhpam7-rhpamcentr`, the `rhpam7-kieserver` and `react-web-app`.
At this point we are interested on the authoring environment. From this page, you can already find a link to open Business Central:

![Credit Card Dispute Project]({% image_path topology-details.png %}){:width="600px"}

4. Click on the link for `cc-dispute-rhpamcentr` (4 Step on image above). That link is the external OpenShift route that allows us to access Business Central. A new tab should open with Business Central login page.

![Business Central Detail]({% image_path business-central-detail.png %}){:width="600px"}

5. You can login in Business Central with the following credentials:
 - user: `developer`{{copy}}
 - password: `developer`{{copy}}

![Business Central Console]({% image_path business-central-console.png %}){:width="600px"}

If you can see the page above, this means you could successfully install a working environment where users can author and test their Business Applications.

Let's head over to have an overview about security within Business Central.
