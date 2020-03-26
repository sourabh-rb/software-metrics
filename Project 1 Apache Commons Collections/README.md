##  Jacoco (Metric 1&2&4):
#### Add mvn dependency to pom.xml:
```xml
<properties>
<commons.jacoco.version>0.8.4</commons.jacoco.version>
</properties>

<plugin>
        <groupId>org.jacoco</groupId>
        <artifactId>jacoco-maven-plugin</artifactId>
        <version>0.8.5</version>
        <executions>
          <execution>
            <id>prepare-agent</id>
            <goals>
              <goal>prepare-agent</goal>
            </goals>
          </execution>
          <execution>
            <id>report</id>
            <phase>prepare-package</phase>
            <goals>
              <goal>report</goal>
            </goals>
          </execution>
          <execution>
            <id>post-unit-test</id>
            <phase>test</phase>
            <goals>
              <goal>report</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
</plugin>
```
#### After adding dependency, do `mvn clean`, `mvn compile`, `mvn test`, report will be generated after the test.

## PITest (Metric 3 only for Version 2.6):
#### Add maven dependency to pom.xml

Steps to Install and Generate PIT via PIT Plugin in Eclipse

1.Installed PIT plugin from Eclipse MarketPlace.
2.Right Click on project and Select Run as --> PIT Mutation score
3.After few minutes you can view your  report in PIT Summary.
4.You can View the report in your workspace--> .metadata--> .plugins --> org.pitest.pitclipse.core --> html_results --> Your Reports (index.html)

- The whole mutation test is super long, around **40-60 minutes**.

## Jdepend (Metric 5):
####Add maven dependency to pom.xml
```xml
<plugin>
        <groupId>org.codehaus.mojo</groupId>
        <artifactId>jdepend-maven-plugin</artifactId>
        <version>2.0</version>
</plugin>
```
Run `mvn site`.