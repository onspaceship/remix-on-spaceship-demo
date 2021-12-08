<p align="center">
  <img src="https://static.onspaceship.com/FullColor.svg" width="100">
</p>

This is a demo for running a [Remix](https://remix.run/) app on [AWS EKS](https://aws.amazon.com/eks/) with automatic deploys from [Spaceship](https://spaceship.run/)

## Prerequisites

- Spaceship:
  - [A Spaceship account](https://onspaceship.com)
  - [The `ship` CLI tool](https://github.com/onspaceship/ship)
- Amazon
  - [An AWS account](https://aws.amazon.com/)
  - [`eksctl`](https://eksctl.io/introduction/#installation)
- [Node 14+](https://nodejs.dev/download/) (for local dev)

## Steps

1. Create the Remix project

   ```
   npm init remix .
   ```

2. Create the cluster

   ```
   eksctl create cluster -n remix-demo -r us-east-2 -t m5a.large
   ```

3. Start up the base demo server in the cluster

   ```
   kubectl apply -f k8s/
   ```

4. Create the cluster entry in Spaceship and install [the Spaceship Agent](https://github.com/onspaceship/agent):

   ```
   Visit: https://onspaceship.com/teams/TEAM_HANDLE/clusters

   Create a new cluster and click the "Need to set up your cluster?" link.

   Copy and run the "kubectl apply" command provided.
   ```
