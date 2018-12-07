# Example

```
<assembly xmlns="http://maven.apache.org/plugins/maven-assembly-plugin/assembly/1.1.3"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:schemaLocation="http://maven.apache.org/plugins/maven-assembly-plugin/assembly/1.1.3 http://maven.apache.org/xsd/assembly-1.1.3.xsd">

    <formats>
        <format>tar.gz</format>
        <format>dir</format>
    </formats>

    <dependencySets>
        <dependencySet>
            <outputDirectory>/lib</outputDirectory>
        </dependencySet>
    </dependencySets>


    <fileSets>
        <fileSet>
            <directory>src/main/resources</directory>
            <outputDirectory>src/main/resources</outputDirectory>
        </fileSet>
    </fileSets>

</assembly>
```