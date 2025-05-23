# nbt-dependency-without-source-test

- For https://github.com/apache/shardingsphere/pull/35476 .
- Execute the following PowerShell 7 command on the `Windows 11` instance with `PowerShell/PowerShell`,
  `version-fox/vfox`, `git-for-windows/git`, `Microsoft.VisualStudio.2022.Community` installed.

```shell
vfox add java
vfox install java@22.0.2-graalce
vfox use --global java@22.0.2-graalce

git clone git@github.com:linghengqian/nbt-dependency-without-source-test.git
cd ./nbt-dependency-without-source-test/
./mvnw clean test -T 1C
./mvnw -PnativeTestInCustom -e -T 1C clean test
```

- The log is as follows,

```shell
PS D:\TwinklingLiftWorks\git\public\nbt-dependency-without-source-test> ./mvnw -PnativeTestInCustom -e -T 1C clean test
[INFO] Error stacktraces are turned on.
[INFO] Scanning for projects...
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Build Order:
[INFO] 
[INFO] nbt-dependency-without-source-test                                 [pom]
[INFO] module-without-source                                              [jar]
[INFO] main-module                                                        [jar]
[INFO] 
[INFO] Using the MultiThreadedBuilder implementation with a thread count of 16
[INFO] 
[INFO] -----< com.github.linghengqian:nbt-dependency-without-source-test >-----
[INFO] Building nbt-dependency-without-source-test 1.0-SNAPSHOT           [1/3]
[INFO]   from pom.xml
[INFO] --------------------------------[ pom ]---------------------------------
[INFO] 
[INFO] --- clean:3.2.0:clean (default-clean) @ nbt-dependency-without-source-test ---
[INFO] 
[INFO] -----------< com.github.linghengqian:module-without-source >------------
[INFO] Building module-without-source 1.0-SNAPSHOT                        [2/3]
[INFO]   from module-without-source\pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- clean:3.2.0:clean (default-clean) @ module-without-source ---
[INFO]
[INFO] --- resources:3.3.1:resources (default-resources) @ module-without-source ---
[INFO] skip non existing resourceDirectory D:\TwinklingLiftWorks\git\public\nbt-dependency-without-source-test\module-without-source\src\main\resources
[INFO]
[INFO] --- compiler:3.13.0:compile (default-compile) @ module-without-source ---
[INFO] No sources to compile
[INFO]
[INFO] --- resources:3.3.1:testResources (default-testResources) @ module-without-source ---
[INFO] skip non existing resourceDirectory D:\TwinklingLiftWorks\git\public\nbt-dependency-without-source-test\module-without-source\src\test\resources
[INFO]
[INFO] --- compiler:3.13.0:testCompile (default-testCompile) @ module-without-source ---
[INFO] No sources to compile
[INFO]
[INFO] --- surefire:3.5.1:test (default-test) @ module-without-source ---
[INFO] No tests to run.
[INFO]
[INFO] ----------------< com.github.linghengqian:main-module >-----------------
[INFO] Building main-module 1.0-SNAPSHOT                                  [3/3]
[INFO]   from main-module\pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- clean:3.2.0:clean (default-clean) @ main-module ---
[INFO] Deleting D:\TwinklingLiftWorks\git\public\nbt-dependency-without-source-test\main-module\target
[INFO] 
[INFO] --- resources:3.3.1:resources (default-resources) @ main-module ---
[INFO] skip non existing resourceDirectory D:\TwinklingLiftWorks\git\public\nbt-dependency-without-source-test\main-module\src\main\resources
[INFO]
[INFO] --- compiler:3.13.0:compile (default-compile) @ main-module ---
[INFO] No sources to compile
[INFO]
[INFO] --- resources:3.3.1:testResources (default-testResources) @ main-module ---
[INFO] skip non existing resourceDirectory D:\TwinklingLiftWorks\git\public\nbt-dependency-without-source-test\main-module\src\test\resources
[INFO]
[INFO] --- compiler:3.13.0:testCompile (default-testCompile) @ main-module ---
[INFO] Recompiling the module because of changed source code.
[INFO] Compiling 1 source file with javac [debug target 22] to target\test-classes
[INFO] 
[INFO] --- surefire:3.5.1:test (default-test) @ main-module ---
[WARNING]  Parameter 'systemProperties' is deprecated: Use systemPropertyVariables instead.
[INFO] Surefire report directory: D:\TwinklingLiftWorks\git\public\nbt-dependency-without-source-test\main-module\target\surefire-reports
[INFO] Using auto detected provider org.apache.maven.surefire.junitplatform.JUnitPlatformProvider
[INFO] 
[INFO] -------------------------------------------------------
[INFO]  T E S T S
[INFO] -------------------------------------------------------
[INFO] Running com.github.linghengqian.SimpleTest
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.033 s -- in com.github.linghengqian.SimpleTest
[INFO] 
[INFO] Results:
[INFO]
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0
[INFO]
[INFO]
[INFO] --- native:0.10.6:test (test-native) @ main-module ---
[INFO] ====================
[INFO] Initializing project: main-module
[INFO] ====================
[INFO] Found GraalVM installation from GRAALVM_HOME variable.
[INFO] Downloaded GraalVM reachability metadata repository from file:/C:/Users/lingh/.m2/repository/org/graalvm/buildtools/graalvm-reachability-metadata/0.10.6/graalvm-reachability-metadata-0.10.6-repository.zip
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Summary for nbt-dependency-without-source-test 1.0-SNAPSHOT:
[INFO]
[INFO] nbt-dependency-without-source-test ................. SUCCESS [  0.083 s]
[INFO] module-without-source .............................. SUCCESS [  0.376 s]
[INFO] main-module ........................................ FAILURE [  1.593 s]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  2.489 s (Wall Clock)
[INFO] Finished at: 2025-05-23T23:15:13+08:00
[INFO] ------------------------------------------------------------------------
[ERROR] Failed to execute goal org.graalvm.buildtools:native-maven-plugin:0.10.6:test (test-native) on project main-module: Missing jar-file for com.github.linghengqian:module-without-source:jar:1.0-SNAPSHOT:test. Ensure that native-maven-plugin runs in package phase. -> [Help 1]
org.apache.maven.lifecycle.LifecycleExecutionException: Failed to execute goal org.graalvm.buildtools:native-maven-plugin:0.10.6:test (test-native) on project main-module: Missing jar-file for com.github.linghengqian:module-without-source:jar:1.0-SNAPSHOT:test. Ensure that native-maven-plugin runs in package phase.
    at org.apache.maven.lifecycle.internal.MojoExecutor.doExecute2 (MojoExecutor.java:333)
    at org.apache.maven.lifecycle.internal.MojoExecutor.doExecute (MojoExecutor.java:316)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute (MojoExecutor.java:212)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute (MojoExecutor.java:174)
    at org.apache.maven.lifecycle.internal.MojoExecutor.access$000 (MojoExecutor.java:75)
    at org.apache.maven.lifecycle.internal.MojoExecutor$1.run (MojoExecutor.java:162)
    at org.apache.maven.plugin.DefaultMojosExecutionStrategy.execute (DefaultMojosExecutionStrategy.java:39)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute (MojoExecutor.java:159)
    at org.apache.maven.lifecycle.internal.LifecycleModuleBuilder.buildProject (LifecycleModuleBuilder.java:105)
    at org.apache.maven.lifecycle.internal.builder.multithreaded.MultiThreadedBuilder$1.call (MultiThreadedBuilder.java:193)
    at org.apache.maven.lifecycle.internal.builder.multithreaded.MultiThreadedBuilder$1.call (MultiThreadedBuilder.java:180)
    at java.util.concurrent.FutureTask.run (FutureTask.java:317)
    at java.util.concurrent.Executors$RunnableAdapter.call (Executors.java:572)
    at java.util.concurrent.FutureTask.run (FutureTask.java:317)
    at java.util.concurrent.ThreadPoolExecutor.runWorker (ThreadPoolExecutor.java:1144)
    at java.util.concurrent.ThreadPoolExecutor$Worker.run (ThreadPoolExecutor.java:642)
    at java.lang.Thread.run (Thread.java:1570)
Caused by: org.apache.maven.plugin.MojoExecutionException: Missing jar-file for com.github.linghengqian:module-without-source:jar:1.0-SNAPSHOT:test. Ensure that native-maven-plugin runs in package phase.
    at org.graalvm.buildtools.maven.AbstractNativeImageMojo.processArtifact (AbstractNativeImageMojo.java:302)
    at org.graalvm.buildtools.maven.AbstractNativeImageMojo.processSupportedArtifacts (AbstractNativeImageMojo.java:285)
    at org.graalvm.buildtools.maven.AbstractNativeImageMojo.addArtifactToClasspath (AbstractNativeImageMojo.java:314)
    at org.graalvm.buildtools.maven.AbstractNativeImageMojo.addDependenciesToClasspath (AbstractNativeImageMojo.java:366)
    at org.graalvm.buildtools.maven.NativeTestMojo.addDependenciesToClasspath (NativeTestMojo.java:122)
    at org.graalvm.buildtools.maven.AbstractNativeImageMojo.populateClasspath (AbstractNativeImageMojo.java:423)
    at org.graalvm.buildtools.maven.AbstractNativeImageMojo.getClasspath (AbstractNativeImageMojo.java:430)
    at org.graalvm.buildtools.maven.AbstractNativeImageMojo.getBuildArgs (AbstractNativeImageMojo.java:201)
    at org.graalvm.buildtools.maven.AbstractNativeImageMojo.buildImage (AbstractNativeImageMojo.java:447)
    at org.graalvm.buildtools.maven.NativeTestMojo.execute (NativeTestMojo.java:169)
    at org.apache.maven.plugin.DefaultBuildPluginManager.executeMojo (DefaultBuildPluginManager.java:126)
    at org.apache.maven.lifecycle.internal.MojoExecutor.doExecute2 (MojoExecutor.java:328)
    at org.apache.maven.lifecycle.internal.MojoExecutor.doExecute (MojoExecutor.java:316)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute (MojoExecutor.java:212)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute (MojoExecutor.java:174)
    at org.apache.maven.lifecycle.internal.MojoExecutor.access$000 (MojoExecutor.java:75)
    at org.apache.maven.lifecycle.internal.MojoExecutor$1.run (MojoExecutor.java:162)
    at org.apache.maven.plugin.DefaultMojosExecutionStrategy.execute (DefaultMojosExecutionStrategy.java:39)
    at org.apache.maven.lifecycle.internal.MojoExecutor.execute (MojoExecutor.java:159)
    at org.apache.maven.lifecycle.internal.LifecycleModuleBuilder.buildProject (LifecycleModuleBuilder.java:105)
    at org.apache.maven.lifecycle.internal.builder.multithreaded.MultiThreadedBuilder$1.call (MultiThreadedBuilder.java:193)
    at org.apache.maven.lifecycle.internal.builder.multithreaded.MultiThreadedBuilder$1.call (MultiThreadedBuilder.java:180)
    at java.util.concurrent.FutureTask.run (FutureTask.java:317)
    at java.util.concurrent.Executors$RunnableAdapter.call (Executors.java:572)
    at java.util.concurrent.FutureTask.run (FutureTask.java:317)
    at java.util.concurrent.ThreadPoolExecutor.runWorker (ThreadPoolExecutor.java:1144)
    at java.util.concurrent.ThreadPoolExecutor$Worker.run (ThreadPoolExecutor.java:642)
    at java.lang.Thread.run (Thread.java:1570)
[ERROR]
[ERROR] Re-run Maven using the -X switch to enable full debug logging.
[ERROR]
[ERROR] For more information about the errors and possible solutions, please read the following articles:
[ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/MojoExecutionException
[ERROR]
[ERROR] After correcting the problems, you can resume the build with the command
[ERROR]   mvn <args> -rf :main-module
```
