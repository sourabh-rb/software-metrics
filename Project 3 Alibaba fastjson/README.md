## JUnit
#### Added junit dependency in pom.xml 
```xml
<dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.10</version>
      <scope>test</scope>
    </dependency>
```

##  Jacoco (Metric 1&2&4):
#### Add mvn dependency to pom.xml:
```xml
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
            <id>post-unit-test</id>
            <phase>test</phase>
            <goals>
              <goal>report</goal>
            </goals>
            <configuration>
              <!--Sets the path to the file which contains the execution data.-->
              <dataFile>target/jacoco.exec</dataFile>
              <!--Sets the output directory for the code coverage report.-->
              <outputDirectory>target/jacoco-ut</outputDirectory>
            </configuration>
          </execution>
        </executions>
      </plugin>
</plugin>
```
#### After adding dependency, do `mvn clean`, `mvn test`, report will be generated after the test.

## PITest (Metric 3):
#### Add maven dependency to pom.xml
```xml
 <plugin>
		<groupId>org.pitest</groupId>
		<artifactId>pitest-maven</artifactId>
		<version>1.4.10</version>
		 <configuration>
				<targetClasses>
				<param>com.alibaba.fastjson*</param>
				</targetClasses>
				<targetTests>
				<param>com.alibaba.fastjson*</param>
				</targetTests>
        <!--These Test Classes are excluded because they fail everytime and causes errors in PITest to run correctly-->
					<excludedTestClasses>
						<param>com.alibaba.json.bvt.issue_1900.Issue1955</param>
						<param>com.alibaba.json.bvt.issue_1900.Issue1901</param>
						<param>com.alibaba.json.bvt.parser.autoType.AutoTypeTest5</param>
						<param>com.alibaba.json.bvt.kotlin.Zoujing</param>
					</excludedTestClasses>
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
#### After adding dependency, do `mvn clean`, `mvn test`, report will be generated after the test.
- The whole mutation test is super long, around **2 hours**.

## Jdepend (Metric 5):
####Add maven dependency to pom.xml
```xml
<plugin>
  <groupId>org.codehaus.mojo</groupId>
  <artifactId>jdepend-maven-plugin</artifactId>
  <version>2.0</version>
  <executions>
    <execution>
      <id>jdepend-report</id>
      <phase>test</phase>
      <goals>
        <goal>generate</goal>
      </goals>
    </execution>
  </executions>
  <configuration>
    <outputDirectory>target/jdepend-report</outputDirectory>
  </configuration>
</plugin>
```
#### After adding dependency, do `mvn clean`, `mvn test`, report will be generated after the test.
