# Deployment

Once an application is ready for production it is time for deployment. There are
various different deployment strategies, but here is an overview of a few
different ones.

## Linux server

The old school hosting option is to roll your own Linux server. This gives you
full control but requires you to manually perform maintenance such as security
updates. It is not playing as nicely with CI/CD as e.g. Cloud Foundry.

## Cloud foundry

Cloud Foundry is a technology for building and deploying apps directly from
source code. A Cloud Foundry service analyzes your code to see what language it
is and then employs a suiting buildpack (a script for compiling the app). It
then configures the app, does some health checks and deploys it. Examples of
providers of Cloud Foundry are: Heroku and IBM.

## Docker Swarm

_Docker swarm has been deprecated and should not be used for new projects_

Docker swarm allows one run a swarm of Docker containers. It is similar to
Docker compose, but more suitable to deployment as it features orchestration and
cluster management. It is not as full-fledged (and as complicated) as
Kubernetes.

## Kubernetes

[Kubernetes](kubernetes) is a technology mainly for deploying Docker images and
does load balancing, handling worker nodes and all for you.
