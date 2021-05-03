# java-repository-template

### How to finish setting up java repository

* Register repository to [codecov.io](https://app.codecov.io/).
* Create badge for code coverage. Copy from:`https://app.codecov.io/gh/<user>/<repository>/settings/badge`
* Add JaCoCo to your project to properly generate coverage report. [Click](#Exemplary JaCoCo plugin configuration:)
* Fill proper username/app_name in `.github/workflows/release.yml` and add `DOCKERHUB_USERNAME` and `DOCKERHUB_TOKEN` secrets
* Add `revision` parameter to your pom.xml file: 
```xml 
  <version>${revision}</version>
  <properties>
  ...
    <revision>0.0.1</revision>
  ...
  </properties>
```
* Create badge for CI action

```
![CI/CD](https://github.com/<user>/<repository>/actions/workflows/ci.yml/badge.svg)
```

* In case of integration tests with real database see exemplary service in `.github/workflows/ci.yml`

### Exemplary JaCoCo plugin configuration:
```xml
<plugin>
    <groupId>org.jacoco</groupId>
    <artifactId>jacoco-maven-plugin</artifactId>
    <version>0.8.6</version>
    <executions>
        <execution>
            <goals>
                <goal>prepare-agent</goal>
                <goal>prepare-agent-integration</goal>
                <goal>report</goal>
                <goal>report-integration</goal>
            </goals>
        </execution>
    </executions>
</plugin>
```
### Exemplary failsafe plugin configuration
```xml
<plugin>
    <artifactId>maven-failsafe-plugin</artifactId>
    <executions>
        <execution>
            <goals>
                <goal>integration-test</goal>
                <goal>verify</goal>
            </goals>
        </execution>
    </executions>
</plugin>
```