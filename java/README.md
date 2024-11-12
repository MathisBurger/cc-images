# Java image

You can run any java code for CodeCanvas with this image, but the choice of libs is currently pretty limited. For detailed view, see all dependencies of pom.xml

Currently supported:
- `junit4`
- `openjfx`


# Command usage

If you want to test your code with junit you will have to use `mvn test -o`

Your `pom.xml` should also reference the local maven repository, because the container will have no internet connection.
The location is at `file:///dependencies`.

For the use of `openjfx` you will have to add following plugin to your `pom.xml`

```xml
<plugin>
    <groupId>org.codehaus.mojo</groupId>
    <artifactId>exec-maven-plugin</artifactId>
    <version>3.1.0</version>
    <configuration>
        <mainClass>com.example.MainApp</mainClass> <!-- Replace with your main class -->
        <arguments>
            <!-- VM options for JavaFX -->
            <argument>--module-path</argument>
            <argument>${project.build.directory}/../.m2/repository/org/openjfx</argument>
            <argument>--add-modules</argument>
            <argument>javafx.controls,javafx.fxml</argument>
        </arguments>
    </configuration>
</plugin>
```