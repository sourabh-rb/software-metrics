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

## PITest (Metric 3):
Add maven dependency to pol.xml
```xml
<properties>
<pitest.version>1.4.10</pitest.version>
</properties>

<plugin>
        <groupId>org.pitest</groupId>
        <artifactId>pitest-maven</artifactId>
        <version>${pitest.version}</version>
        <configuration>
          <targetClasses>
            <param>org.apache.commons.configuration2.*</param>
          </targetClasses>
          <targetTests>
            <param>org.apache.commons.configuration2.*</param>
          </targetTests>
        </configuration>
        <executions>
          <execution>
            <id>pit-report</id>
            <phase>test</phase>
            <goals>
              <goal>mutationCoverage</goal>
            </goals>
          </execution>
        </executions>
</plugin>
```
- After adding dependency, run `mvn -Drat.skip=true test`. Here we must add `-Drat.skip=true`, because there are two many licence problems so that mvn test cannot ignore.

- The whole mutation test is super long, around **40 minutes**.

## Jdepend (Metric 5):
Add maven dependency to pom.xml
```xml
<plugin>
        <groupId>org.codehaus.mojo</groupId>
        <artifactId>jdepend-maven-plugin</artifactId>
        <version>2.0</version>
</plugin>
```
Run `mvn site`.