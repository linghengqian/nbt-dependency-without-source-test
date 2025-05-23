# nbt-dependency-without-source-test

- For https://github.com/apache/shardingsphere/pull/35476 .
- Execute the following PowerShell 7 command on the `Windows 11` instance with `PowerShell/PowerShell`,
  `version-fox/vfox`, `git-for-windows/git` installed.

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

```
