# protoc-plugin
maven plugin to generate java sources from protobuf

It is for of [maven-protoc-plugin](https://github.com/dtrott/maven-protoc-plugin).

**********************************************
*** Maven Protocol Buffers (protoc) Plugin ***
**********************************************

A minimal configuration to invoke this plugin would be:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.mycompany.example</groupId>
    <artifactId>example-protoc</artifactId>
    <packaging>jar</packaging>
    <version>1.0-SNAPSHOT</version>
    <name>protoc-example</name>
    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <configuration>
                    <source>1.7</source>
                    <target>1.7</target>
                </configuration>
            </plugin>
            <plugin>
                <groupId>com.google.protobuf.tools</groupId>
                <artifactId>maven-protoc-plugin</artifactId>
                <configuration>
                    <!-- Protobuff executable -->
                    <protocExecutable>/usr/local/bin/protoc</protocExecutable>
                    <!-- Will drop previously created output directory. By default false -->
                    <cleanOutputDirectory>false</cleanOutputDirectory>
                </configuration>
                <executions>
                    <execution>
                        <goals>
                            <goal>compile</goal>
                            <goal>testCompile</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </build>
    <dependencies>
        <dependency>
            <groupId>com.google.protobuf</groupId>
            <artifactId>protobuf-java</artifactId>
            <version>2.3.0</version>
        </dependency>
    </dependencies>
</project>
```

Everything should then build with a: mvn clean install,
besides that you can create a special profile for the source generation and use command: mvn -Pyour_profile generate-sources  
