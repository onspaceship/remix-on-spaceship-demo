<p align="center">
  <img src="https://static.onspaceship.com/FullColor.svg" width="100">
</p>

This is a demo for running a [Remix](https://remix.run/) app on [AWS EKS](https://aws.amazon.com/eks/) with automatic deploys from [Spaceship](https://spaceship.run/)

**⚠️ WIP ⚠️** We're working to make this an even simpler process in the future (less steps!), so keep checking back regularly for updates.

## Prerequisites

- Spaceship:
  - [A Spaceship account](https://onspaceship.com)
  - [The `ship` CLI tool](https://github.com/onspaceship/ship)
- Amazon
  - [An AWS account](https://aws.amazon.com/)
  - [`eksctl`](https://eksctl.io/introduction/#installation)
- [Node 14+](https://nodejs.dev/download/) (for local dev)

## Steps

0. ### [Create a fork of this project](https://github.com/onspaceship/remix-demo/fork)

1. ### Create the Remix project

   ```
   npm init remix .
   # Choose the "Remix App Server" when prompted

   git add .
   git commit -m '🚀 Welcome to the Remix on Spaceship Demo!'
   ```

2. ### Create the cluster

   ```
   eksctl create cluster -n remix-demo -r us-east-2 -t m5a.large
   # Feel free to change the node sizes or region to suit your needs
   ```

3. ### Create the cluster entry in Spaceship and install [the Spaceship Agent](https://github.com/onspaceship/agent):

   Visit: https://onspaceship.com/teams/TEAM_HANDLE/clusters

   Create a new cluster and click the "Need to set up your cluster?" link.

   Copy and run the `kubectl apply` command provided.

4. ### Start up the base demo server in the cluster

   ```
   kubectl apply -f k8s/
   ```

5. ### Create an app in Spaceship and set it up for delivery:

   Visit: https://onspaceship.com/teams/TEAM_HANDLE/apps/new

   Install the GitHub App, if you haven't already.

   Find your repo and create an app with it.

   On the app's main page, choose Builds and Delivery and proceed through all 3 steps. We'll set up the deployment label next.

6. ### Add the delivery label

   ```
   ship setup-delivery remix-demo -a remix-demo -t TEAM_HANDLE
   ```

7. ### Change some code and push to GitHub

   Load up `app/routes/index.tsx` and make some changes to the page. Then push them up to GitHub.

8. ### See your changes live on the web! 🚀

   Once the delivery completes on Spaceship, you can visit the running application to see your changes. You can get the temporary address to your application by running this command:

   ```
   kubectl get svc remix-demo
   ```

   It will be the address ending in `*.elb.amazonaws.com`. Make sure the URL in your browser starts with `http://`
