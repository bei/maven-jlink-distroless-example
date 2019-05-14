# maven-jlink-distroless-example

This project shows how you can build a tiny Docker image based on the google [distroless](https://github.com/GoogleContainerTools/distroless) docker base image with a custom modular Java run-time image for your app.

After building the docker image you can start it with

```
docker run agilhard/maven-jlink-distroless-example
```

## Prerequisites

- [JDK](http://jdk.java.net/)
- [Maven](https://maven.apache.org/)
- [Docker](https://www.docker.com/)

**You will need at least Java 9:** This project uses [jlink](https://docs.oracle.com/javase/9/tools/jlink.htm) to assemble modules and their dependencies into a custom Java run-time image.

## Caveats

[maven-jlink-plugin](https://maven.apache.org/plugins/maven-jlink-plugin/) is still in alpha version and have some issues:

- The current version avaiable at Maven Central repository (3.0.0-alpha-1) has a bug (See: [MJLINK-4](https://issues.apache.org/jira/browse/MJLINK-4)). We're using a SNAPSHOT version (3.0.0-alpha-2) and unpredictable errors may occur with SNAPSHOT updates.
- JDK `jmods` folder is always relative to `jlink` binary location and the generated Java run-time image may NOT be compatible with the Docker base image (See: [MJLINK-6](https://issues.apache.org/jira/browse/MJLINK-6)).

[maven-jar-plugin](https://maven.apache.org/plugins/maven-jar-plugin/) don't know how to define a module with a main-class (See: [MJAR-238](https://issues.apache.org/jira/projects/MJAR/issues/MJAR-238)).

## Use the newer other example instead ;-)

This example here worked when it was created some time ago.

It may no longer work now due to incompatible changes on the Source Code of the [maven-jlink-plugin](https://maven.apache.org/plugins/maven-jlink-plugin/) in the meantime.

There is another example of doing this which is using a forked and enhanced version of that maven-jlink-plugin, the [jlink-jpackager-maven-plugin](https://github.com/agilhard-oss/jlink-jpackager-maven-plugin).

This other example is guaranteed to work better and should work still.

You can find it here: [jlink-distroless-maven-example](https://github.com/agilhard-oss/jlink-distroless-maven-example).



