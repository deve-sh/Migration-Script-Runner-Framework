# Setup the framework for running scripts

If most of your scripts have been written and run on your machine, this is going to feel new.

At larger tech teams, you might write your scripts on your machine but very seldom would you be able to run them from your machines - Even for environments such as dev, staging or preview.

The reason? Your machine doesn't have authorization to the private cloud running your databases or infrastructure. At the point a company has matured to a handful of users, they would obviously switch to a private subnet where access is then restricted to tooling such as Bastion in AWS or via an internet gateway that allows very specific traffic and commands to pierce through to your subnets.

As a result, you're left with a single option: Write scripts locally or on the cloud BUT always run them from an instance or a CI/CD pipeline such as CircleCI or GitHub Actions that has limited access to your cloud resources (obviously) or on a private instance that gets spun up on demand (Think of it as a Lambda on AWS or a Compute Engine instance on Google Cloud) inside your VPC and has limited access to your cloud resources.

This could be something as simple as:
- A GitHub Action script that can be invoked on demand, takes the branch and the filename to run and proceeds.
- A cluster of instances that is spun up on demand, which clones the scripts from your repository and runs them - Logs the output of these scripts to something like Google Cloud Logging or CloudWatch.

### Why this is important and useful

- This forces you to version control and peer-review your scripts anyway - As in order to even test these scripts, you have to commit them to version control and run them on a pipeline.
- CI/CD Pipelines do not have network issues/drops or power outages (If they do, you might want to check if your database instance itself is online or not as these outages are usually cloud-wide outages).
- Secrets can be stored safely in a Secrets Manager provided by the Cloud Provider or the CI/CD provider, so there's no need to hardcode - Enhancing security by default.
- There's now a trace of each run and each resource modified by this as Cloud/CI providers have extensive resource logging - which can be used as an accountability driver for large engineering teams.
- There's a bandwidth related advantage which we'll discuss in the next step.

> There obviously will be some inhibition when it comes to running even the most basic scripts on a pipeline. But trust me, the benefits of historical context, accountability and reliability of the environment far outweigh the costs.
