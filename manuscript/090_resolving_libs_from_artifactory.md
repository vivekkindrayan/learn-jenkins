# Using Artifactory To Resolve Artifacts

## Introduction to Artifactory

Following video explains the usefulness of Artifactory to share libraries and artifacts in a collaborated development.

[![Introduction ro Artifactory](images/chap9/artifactory_intro.png)](https://youtu.be/aa4YBDUDWy0 "Introduction to Artifactory")

In addition, Artifactory could be used as a local repository for storing rpms, debs, docker images, gems, pythong packages etc.

## Integrating Artifactory with Jenkins

Artifactory could be used for two purposes,
1. Resolving Libraries/Packages From
1. Pushing build artifacts to

In this chapter, we are going to start using Artifactory as a local repository  to resolve libraries from.

In order to connect Artifactory with Jenkins, first step is t install the Plugin.

![Installing Artifactory Plugin](images/chap9/artifactory_plugin.jpg)

From Manage Plugins, lets filter by "Artifactory", select the relevant plugin and install it.

Following is a screenshot of the Artifactory console

![ Artifactory Console](images/chap9/artifactory_login.jpg)



## Configure Artifactory Plugin
* Manage Jenkins -> Configure System -> Artifactory -> Add
* Add Artifactory details and Test Connection

e.g.
   uri: http://HOSTNAME:8081/artifactory
   port: 8081
   user: admin
   pass: password


![Configuring  Artifactory Plugin](images/chap9/artifactory_configs.jpg)


## Resolve Artifacts from Artifactory

Configure build job, and from build environment select **Resolve artifacts from Artifactory**. Click on **Refresh Repositories** which should auto select repositories. For snapshots, use libs-snapshot as repo name.


![Resolve Artifacts from   Artifactory ](images/chap9/resolve.png)

Validate that the artifacts are being resolved from Artifactory by running a new building and checking the console output.


```

[output snippet]


[INFO] Downloaded: http://52.39.130.66:8081/artifactory/libs-release/org/apache/maven/plugins/maven-plugins/23/maven-plugins-23.pom (0 B at 0.0 KB/sec)
[INFO] Downloading: http://52.39.130.66:8081/artifactory/libs-release/org/apache/maven/maven-parent/22/maven-parent-22.pom
[INFO] Downloaded: http://52.39.130.66:8081/artifactory/libs-release/org/apache/maven/maven-parent/22/maven-parent-22.pom (0 B at 0.0 KB/sec)


```
