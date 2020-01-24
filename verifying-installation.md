# Verifying your installation

So far you have requested in your self-service console a working environment to author process and policies. Now we will verify the environment and the tools available to you. Earlier we saw that Red Hat Process Automation Manager has authoring tools both for developers as well as subject domain experts.

![Collaboration Tools]({% image_path collaboration_tools.png %}){:width="600px"}

For business experts, the platform provides the Business Central console, a web-based business workbench with capabilities to manage the full lifecycle of your automation assets.

## Business Central

Let's test business central on the environment you just installed.

1. Go to your OpenShift console tab. Go to step 2 if you're already logged in. If you're not yet logged in, or have been logged out, login using the same credentials as before:

- user: `userX`{{copy}}
- password: `openshift`{{copy}}

![OpenShift Console]({% image_path openshift-console.png %}){:width="600px"}

2. Make sure you are on the `Developer` perspective and that you have the `credit-card-dispute` project selected. On the left menu, select the `Topology` option.

3. You will see listed 2 components the `cc-dispute-kieserver` and the `cc-dispute-rhpamcentr`. All you need to know is that the first one is for execution of your automation assets and the latter for authoring of your automation assets.
At this point we are interested on the authoring environment. From this page, you can already find a link to open Business Central:

![Credit Card Dispute Project]({% image_path topology-details.png %}){:width="600px"}

4. Click on the link for `cc-dispute-rhpamcentr` (4 Step on image above). That link is the external OpenShift route that allows us to access Business Central. A new tab should open with Business Central login page.

![Business Central Detail]({% image_path business-central-detail.png %}){:width="600px"}

5. You can login in Business Central with the following credentials:
 - user: `developer`{{copy}}
 - password: `developer`{{copy}}

And you should see the console as follows:

![Business Central Console]({% image_path business-central-console.png %}){:width="600px"}
