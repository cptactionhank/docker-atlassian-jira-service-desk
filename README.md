# Atlassian JIRA Service Desk in a Docker container

> Version 3.0.4

[![Build Status](https://img.shields.io/circleci/project/cptactionhank/docker-atlassian-jira-service-desk/3.0.4.svg)](https://circleci.com/gh/cptactionhank/docker-atlassian-jira-service-desk) [![Open Issues](https://img.shields.io/github/issues/cptactionhank/docker-atlassian-jira-service-desk.svg)](https://github.com/cptactionhank/docker-atlassian-jira-service-desk) [![Stars on GitHub](https://img.shields.io/github/stars/cptactionhank/docker-atlassian-jira-service-desk.svg)](https://github.com/cptactionhank/docker-atlassian-jira-service-desk) [![Forks on GitHub](https://img.shields.io/github/forks/cptactionhank/docker-atlassian-jira-service-desk.svg)](https://github.com/cptactionhank/docker-atlassian-jira-service-desk) [![Stars on Docker Hub](https://img.shields.io/docker/stars/cptactionhank/atlassian-jira-service-desk.svg)](https://registry.hub.docker.com/u/cptactionhank/atlassian-jira-service-desk) [![Pulls on Docker Hub](https://img.shields.io/docker/pulls/cptactionhank/atlassian-jira-service-desk.svg)](https://registry.hub.docker.com/u/cptactionhank/atlassian-jira-service-desk)

* [Atlassian JIRA Core](https://github.com/cptactionhank/docker-atlassian-jira)
* [Atlassian JIRA Software](https://github.com/cptactionhank/docker-atlassian-jira-software)
* [Atlassian JIRA Service Desk](https://github.com/cptactionhank/docker-atlassian-jira-service-desk)
* [Atlassian JIRA Confluence](https://github.com/cptactionhank/docker-atlassian-confluence)

A containerized installation of Atlassian JIRA Service Desk setup with a goal of keeping the installation as default as possible, but with a few Docker related twists.

Want to help out, check out the contribution section.

## I'm in the fast lane! Get me started

To quickly get started with running a JIRA Service Desk instance, first run the following command:
```bash
docker run --detach --publish 8080:8080 cptactionhank/atlassian-jira-service-desk:3.0.4
```

Then use your browser to navigate to `http://[dockerhost]:8080` and finish the configuration.

## The slower road to get started

For a more in-depth documentation on how to get started please visit the website made for this purpose. [cptactionhank.github.io/docker-atlassian-jira-service-desk](https://cptactionhank.github.io/docker-atlassian-jira-service-desk)

## Contributions

This has been made with the best intentions and current knowledge and thus it shouldn't be expected to be flawless. However you can support this repository with best-practices and other additions. Circle-CI has been setup to build the Dockerfile and run acceptance tests on the Atlassian JIRA Service Desk image to ensure it is working.

Circle-CI has been setup to automatically deploy new version branches when successfully building a new version of Atlassian JIRA Service Desk in the `master` branch and serves as the base. Furthermore an `eap` branch has been setup to automatically build and commit updates to ensure the `eap` branch contains the latest version of Atlassian JIRA Service Desk Early Access Preview.

Out of date documentation, lack of tests, etc. you can help out by either creating an issue and open a discussion or sending a pull request with modifications to the appropriate branch.

Acceptance tests are performed by Circle-CI with Ruby using the RSpec, Capybara, and PhantomJS frameworks.
