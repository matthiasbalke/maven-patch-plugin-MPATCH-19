# maven-patch-plugin-MPATCH-19

This repository contains an minimal example for issue [MPATCH-19](https://issues.apache.org/jira/browse/MPATCH-19) of the [maven-patch-plugin](https://github.com/apache/maven-patch-plugin).


## expected behaviour

1) The ignored file should be logged as ignored
1) The `test.patch` should be logged as applied
1) The `test.patch` should be applied
1) the build should be successful
1) The content of `target/generated-sources/MyClass.java` should equal
```java
public class MyClass {
    public static void main(String[] args) {
        System.out.println("This was patched by test.patch!");
    }
}
```

## actual behaviour
1) The `ignored.patch` is applied
1) The patch `test.patch` fails
1) The build fails
1) The content of `target/generated-sources/MyClass.java` equals
```java
public class MyClass {
    public static void main(String[] args) {
        System.out.println("This was patched by ignored.patch!");
    }
}
```
