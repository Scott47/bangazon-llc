# Digital Ocean Deploy

First, if you haven't used Digital Ocean yet, [sign up for $100 credit](https://m.do.co/c/47e5e578d1cd) which is good for 60 days. Deploying your first three static sites is cost free, and deploying a small Django app is only $5.00 per month, so you get two months of having a deployed API on credit.

Your React app is considered a static app, so you won't be charged for it, unless you go over your 3 free static deployed apps.

## Deploy React Client

1. Fork your team's Rare client project repository to your own account.
1. In Digital Ocean, create an app.
1. Click the Github icon.
1. Choose your repository from the search field that appears.
1. Click next.
1. It will auto-detect that you're trying to deploy a **Web Service**. Click `Edit` and change the type to **Static Site**.
1. Click next.
1. Type in a name like "levelup-steve" or anything else that works.
1. Click next.
1. Make sure **Starter Plan** is chosen.
1. Click **Launch Starter App**.

Now wait for a few minutes while your application is built and deployed. Once successful, you can [deploy your Django API](./CLOUD_DIGITAL_OCEAN.md).

