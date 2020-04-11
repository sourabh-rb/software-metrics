## *Software Measurement Project - SOEN 6611-2184-D (Winter 2020)*
-------------------------------------------------------

The aim of this project is to calculate several software metrices and to define correlation between them.

## Team Member Details
| Name | Student ID | Email ID |
| --- | --- | --- |
| Haifeng Wu | 40102956 | hanfordwu@gmail.com |
| Sourabh Rajeev Badagandi | 40098471 | sourabh.rajeev@gmail.com |
| Sandeep Kaur Ranote  | 40089795 |ranote9466@gmail.com |
| Basant Gera | 40082433 | basantgera29@gmail.com |
| Meet Patel  | 40071820 | 91meetpatel@gmail.com|


## We calculated following metrices.


1. **Statement Coverage:** Statement coverage is a white box testing technique, which involves the execution of all the statements at least once in the source code. It is a metric, which is used to calculate and measure the number of statements in the source code which have been executed.
2. **Branch Coverage:** ranch coverage is a testing method, which aims to ensure that each one of the possible branch from each decision point is executed at least once and thereby ensuring that all reachable code is executed.
3. **Mutation Score:** Mutation testing is used to design new software tests and evaluate the quality of existing software tests.
4. **Cyclomatic Complexity: McCabe Complexity** Cyclomatic complexity is a software metric used to indicate the complexity of a program. It is a quantitative measure of the number of linearly independent paths through a program's source code. 
5. **Package Instability** : This metric is used to measure the relative susceptibility of class to changes. According to the definition instability is the ration of outgoing dependencies to all package dependencies and it accepts value from 0 to 1.
6. **Post Release Defect Density** : Defect Density is the number of defects confirmed in software/module during a specific period of operation or development divided by the size of the software/module. It enables one to decide if a piece of software is ready to be released.

## Selected Open-Source Systems

1. **Apache Common Collections** - [*project details*](https://commons.apache.org/proper/commons-collections/) , [*source-code*](https://github.com/apache/commons-collections) 
2. **Alibaba Fastjson** - [*project details*](https://github.com/alibaba/fastjson/wiki) , [*source-code*](https://github.com/alibaba/fastjson) 
3. **Apache Commons Lang** - [*project details*](http://commons.apache.org/proper/commons-lang/) , [*source-code*](https://github.com/apache/commons-lang)
4. **Apache Commons Configuration** - [*project details*](https://commons.apache.org/proper/commons-configuration/) , [*source-code*](https://github.com/apache/commons-configuration)

## Directory Structure

    ├── Documents Assocaited with Project     # Cover Letter,IEEE Format Paper,Presentation,Updated Proposal
    ├── Project 1 Apache Commons Collections  ├── Correlation Analysis & Data Collection -csv files and raw data #Project 1
    ├── Project 2 Apache commons Lang         ├── Correlation Analysis & Data Collection -csv files and raw data #Project 2
    ├── Project 3 Alibaba fastjson            ├── Correlation Analysis & Data Collection -csv files and raw data #Project 3
    ├── Project 4 Apache Common Configuration ├── Correlation Analysis & Data Collection -csv files and raw data #Project 4
    ├──Replication_Package_Team_H	      ├──IEEE Format paper, Pom.xml files
    └── README.md

## Used tools for different metrices :

### Jacoco (Metric 1&2&4):
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

### PIT - Mutation Testing (Metric 3)
#### Add maven dependency to pom.xml
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
            <param>Pacakage_Name</param>
          </targetClasses>
          <targetTests>
            <param>Pacakage_Name</param>
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

### Jdepend (Metric 5)
####Add maven dependency to pom.xml
```xml
<plugin>
        <groupId>org.codehaus.mojo</groupId>
        <artifactId>jdepend-maven-plugin</artifactId>
        <version>2.0</version>
</plugin>
```
Run `mvn site`.

### CLOC - Counting lines of the program  (Metric 6)

![alt](https://i.imgur.com/3wrTlGx.png)
```
cloc --cloc-1.84.exe fileName.zip
```
## Replication Package URL : https://drive.google.com/drive/folders/1r-KZHGdVDZsa38rsYEvJFlQfW7WT9rIB?usp=sharing
