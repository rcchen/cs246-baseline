# cs246-baseline

An easy way to start Hadoop based assignments in [CS246](https://web.stanford.edu/class/cs246/).

## Requirements

* Java 8 SDK (older versions possible, see FAQ)

This project also includes plugins to auto-configure the project for Eclipse or IntelliJ by running the commands `./gradlew eclipse` or `./gradlew idea` respectively

## Instructions

1. Clone this repository
2. Run the command `./gradlew eclipse`
3. Import the root folder into Eclipse

To run the code you have written, simply call the corresponding Gradle run task. Run tasks are defined in `build.gradle`. A sample run task for `WordCount` is included.

```
task runWordCount(type: JavaExec) {
  dependsOn removeOutput

  main = "edu.stanford.cs246.wordcount.WordCount"
  classpath = sourceSets.main.runtimeClasspath
  args = ["data/pg100.txt", "output"]
}
```

This task is executed by typing in `./gradlew runWordCount` from the root directory. It will automatically delete an output folder if it exists from a previous run, then execute the `WordCount` program with the specified arguments.

To define your own run task, just copy that block, paste it somewhere else in `build.gradle`, and name the task differently. You will also want to change `main` and `args` as appropriate. Everything else can probably be left the same though.

## FAQ

**Is the Java 8 SDK strictly necessary? I have the Java < 8 SDK installed.**

No, it is not necessary. However, there are a ton of features in Java 8 that you might like to use like lambdas. If you want to use an older Java SDK, just change the `sourceCompatibility` line in `build.gradle` to match your installed SDK version.

**Don't we need a cluster to run things for this class?**

Nope. See https://piazza.com/class/ixhxcsxn21l1fu?cid=99

**I don't have Java locally. How do I install it?**

Probably just download the package corresponding to your OS from here: http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
