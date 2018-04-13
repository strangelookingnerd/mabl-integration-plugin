![mabl logo](https://avatars3.githubusercontent.com/u/25963599?s=100&v=4)
# mabl Jenkins Plugin
[![Build Status](https://ci.jenkins.io/job/Plugins/job/mabl-integration-plugin/job/master/7/badge/icon)](https://ci.jenkins.io/job/Plugins/job/mabl-integration-plugin/job/master/7/)

This plugin allows easy launching of [mabl](https://www.mabl.com) journeys as a step in your Jenkins build. Your Jenkins build outcome will be tied to that of your deployment event.

# Plugin Installation
The plugin is not yet available from the Jenkins plugin repo (coming soon), so you will need to build and install from source.

## Building from Source

1. Clone this repo
2. build with `mvn clean package`
3. Copy the plugin in `target/mabl-integration.hpi` to your Jenkins `plugins/` directory
4. Restart Jenkins

You can also install the `.hpi` file from the web UI by visting
**Jenkins > Manage Jenkins > Manager Plugins > Advanced > Upload Plugin**.

## Creating a mabl Build Step

1. Create or edit a Jenkins project
2. Select **Run mabl journeys** from the **Add build step** drop down list
3. Copy your API key, `environment_id`, and `application_id` from the [API Settings Page](https://help.mabl.com/v1.0/docs/triggering-tests-via-the-api)
4. Save and run your build

## Local Development

Overview of how to launch a Jenkins Docker instance with Jenkins, then build the plugin and deploy it that instance.

```bash
# Launch Jenkins
docker run -d -p 9090:8080 --name=jenkins-master jenkins

# Setup your Jenkins instance

# Build and deploy plugin to Jenkins
mvn clean package \
  && docker cp target/mabl-integration.hpi jenkins-master:/var/jenkins_home/ \
  && docker restart jenkins-master
```
