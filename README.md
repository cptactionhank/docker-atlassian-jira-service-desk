[![CircleCI Build Status](https://img.shields.io/circleci/project/cptactionhank/docker-atlassian-jira-service-desk/master.svg?label=CircleCI)](https://circleci.com/gh/cptactionhank/docker-atlassian-jira-service-desk) [![Open Issues](https://img.shields.io/github/issues/cptactionhank/docker-atlassian-jira-service-desk.svg)](https://github.com/cptactionhank/docker-atlassian-jira-service-desk/issues) [![Stars on GitHub](https://img.shields.io/github/stars/cptactionhank/docker-atlassian-jira-service-desk.svg)](https://github.com/cptactionhank/docker-atlassian-jira-service-desk/stargazers) [![Forks on GitHub](https://img.shields.io/github/forks/cptactionhank/docker-atlassian-jira-service-desk.svg)](https://github.com/cptactionhank/docker-atlassian-jira-service-desk/network) [![Stars on Docker Hub](https://img.shields.io/docker/stars/cptactionhank/atlassian-jira-service-desk.svg)](https://hub.docker.com/r/cptactionhank/atlassian-jira-service-desk/) [![Pulls on Docker Hub](https://img.shields.io/docker/pulls/cptactionhank/atlassian-jira-service-desk.svg)](https://hub.docker.com/r/cptactionhank/atlassian-jira-service-desk/)

> HEADS UP! The `latest` tag and versions above 3.10.1 will be switching to use Alpine versions of OpenJDK as the base image.

# Atlassian JIRA Service Desk in a Docker container

This is a containerized installation of Atlassian JIRA Service Desk with Docker, and it's a match made in heaven for us all to enjoy. The aim of this image is to keep the installation as straight forward as possible, but with a few Docker related twists. You can get started by clicking the appropriate link below and reading the documentation.

* [Atlassian JIRA Core](https://cptactionhank.github.io/docker-atlassian-jira)
* [Atlassian JIRA Software](https://cptactionhank.github.io/docker-atlassian-jira-software)
* [Atlassian JIRA Service Desk](https://cptactionhank.github.io/docker-atlassian-jira-service-desk)
* [Atlassian Confluence](https://cptactionhank.github.io/docker-atlassian-confluence)

If you want to help out, you can check out the contribution section further down.

## I'm in the fast lane! Get me started

To quickly get started running a JIRA Service Desk instance, use the following command:
```bash
docker run --detach --publish 8080:8080 cptactionhank/atlassian-jira-service-desk:latest
```

Then simply navigate your preferred browser to `http://[dockerhost]:8080` and finish the configuration.

## Configuration

You can configure a small set of things by supplying the following environment variables

| Environment Variable   | Description |
| ---------------------- | ----------- |
| X_PROXY_NAME           | Sets the Tomcat Connectors `ProxyName` attribute |
| X_PROXY_PORT           | Sets the Tomcat Connectors `ProxyPort` attribute |
| X_PROXY_SCHEME         | If set to `https` the Tomcat Connectors `secure=true` and `redirectPort` equal to `X_PROXY_PORT`   |
| X_PATH                 | Sets the Tomcat connectors `path` attribute |

## Contributions

This image has been created with the best intentions and an expert understanding of docker, but it should not be expected to be flawless. Should you be in the position to do so, I request that you help support this repository with best-practices and other additions.

Travis CI and CircleCI has been configured to build the Dockerfile and run acceptance tests on the Atlassian JIRA Service Desk image to ensure it is working.

Travis CI has additionally been configured to automatically deploy new version branches when successfully building a new version of Atlassian JIRA Service Desk in the `master` branch and serves as the base. Furthermore an `eap` branch has been setup to automatically build and commit updates to ensure this branch contains the latest version of Atlassian JIRA Service Desk Early Access Preview.

If you see out of date documentation, lack of tests, etc., you can help out by either
- creating an issue and opening a discussion, or
- sending a pull request with modifications (remember to read [contributing guide](https://github.com/cptactionhank/docker-atlassian-jira-service-desk/blob/master/CONTRIBUTING.md) before.)

Continuous Integration and Continuous Delivery is made possible with the great services from [GitHub](https://github.com), [Travis CI](https://travis-ci.org/), and [CircleCI](https://circleci.com/) written in [Ruby](https://www.ruby-lang.org/), using [RSpec](http://rspec.info/), [Capybara](https://jnicklas.github.io/capybara/), and [PhantomJS](http://phantomjs.org/) frameworks.

## Building the Docker image

JIRA Service Desk is in a period of fast development, and releases are coming thick and fast. In order to keep up to date, you might have to rebuild this image. Here are the steps to do it

Clone the repository:
```git clone git@github.com:cptactionhank/docker-atlassian-jira-service-desk.git
cd docker-atlassian-jira-service-desk
export PATH=$PATH:$(pwd)/bin
prepare
docker build -t jira-desk .
```

Note: if you get the error:
```error: test is not defined```
then your jq version is too old. Go to `https://stedolan.github.io/jq/` and get a newer version and add it to your PATH before the platform version.

