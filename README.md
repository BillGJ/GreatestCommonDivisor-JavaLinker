# Greatest Common Divisor - Java Linker

This project contains a maven project with a simple class that can calculate the greatest common denominators of a number.
The goal is to use `jlink` to create a custom JRE that can run our jar.

The `GreatestCommonDivisor` folder contains an executable class that calculates the greatest common divisor of two numbers.

1. We created a jar from it executing 

    ```
    mvn clean package
    ```

2. We checked the dependencies of the generated jar with jdeps: 
    ```
    jdeps target/gcd-1.0-SNAPSHOT.jar
    ```

3. We created a custom JRE to run this jar:
    ```
    jlink --module-path "$JAVA_HOME/jmods" --module-path target/classes --add-modules com.udacity.gcd --output tinyJRE
    ```

4. We checked the size of this image
    ```
    du -sh tinyJRE
    ```

5. You can try running the jar with the custom image. 
    ```
    tinyJRE/bin/java -jar target/gcd-1.0-SNAPSHOT.jar 
    ```