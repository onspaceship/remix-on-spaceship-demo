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
