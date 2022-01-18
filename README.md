# example-micronaut

## Building

```
gradle assemble
```

## Running

Please refer to [README](https://github.com/CRaC/docs#users-flow) for details.

### Preparing the image
1. Run the [JDK](README.md#JDK) in the checkpoint mode
```
$JAVA_HOME/bin/java -XX:CRaCCheckpointTo=cr -jar build/libs/example-0.1-all.jar
```
2. Warm-up the instance
```
siege -c 1 -r 100000 -b http://localhost:8080/hello/test
```
3. Request checkpoint
```
jcmd build/libs/example-0.1-all.jar JDK.checkpoint
```

### Restoring

```
$JAVA_HOME/bin/java -XX:CRaCRestoreFrom=cr
```
