# Sample Project Tools

## JaCoCo

### Resources
<del>[JaCoCo gradle docs](https://docs.gradle.org/current/userguide/jacoco_plugin.html)</del>

[JaCoCo gradle simple start](https://reflectoring.io/jacoco/)

[JaCoCo gradle issue resolution](https://github.com/vaskoz/core-java9-impatient/issues/11)

### Installation

```gradle 
plugins {
    id 'java'
    id 'jacoco' //include this line in build.gradle
}

dependencies {
    //should include these dependencies so test coverage can run
    
    implementation 'org.springframework.boot:spring-boot-starter-web'
    testImplementation 'org.springframework.boot:spring-boot-starter-test'
    testImplementation 'org.junit.jupiter:junit-jupiter-api:5.3.1'
    testRuntimeOnly 'org.junit.jupiter:junit-jupiter-engine:5.3.1'
}

test {
    useJUnitPlatform()
}

jacoco {
    toolVersion = "0.8.3"
}

jacocoTestCoverageVerification {
    violationRules {
        rule {
            limit {
                counter = 'LINE'
                value = 'COVEREDRATIO'
                minimum = 1.0
            }
        }
    }
}
```
### Running

To ensure JaCoCo gets installed in your project first run:
```bash
./gradlew build
```

To execute coverage run:
```bash
./gradlew build jacocoTestReport
```

you will be able to find your html coverage report in:
`build/reports/jacoco/test/html/index.html`

## Google Java Style Guide

### Resources
[Google Java Style Guide](https://google.github.io/styleguide/javaguide.html)

[Google Java Format Plugin](https://github.com/google/google-java-format)

[Google Java Format Intellij Plugin](https://plugins.jetbrains.com/plugin/8527-google-java-format)

[Google Java IntelliJ Style File](https://raw.githubusercontent.com/google/styleguide/gh-pages/intellij-java-google-style.xml)

[Spotless Gradle Plugin](https://github.com/diffplug/spotless/tree/master/plugin-gradle#applying-to-java-source-google-java-format)

### Gradle Intallation

```gradle 
plugins {
    id 'java'
    id "com.diffplug.gradle.spotless" version "3.23.0" //include this line in build.gradle
}

spotless {
    java {
        googleJavaFormat()
    }
}
```

### IntelliJ Installation

-[ ] Go to `Preferences/Settings-> Plugins -> browse repositories` and search for `google-java-format`
-[ ] Install the plugin.
-[ ] Restart IntelliJ.
-[ ] Go to `Preferences/Settings-> Other Settings-> google-java-format Settings` and `enable google-java-format`
-[ ] download and save [Google Java IntelliJ Style File](https://raw.githubusercontent.com/google/styleguide/gh-pages/intellij-java-google-style.xml)
-[ ] Go to `Preferences/Settings-> Settings-> Editor -> CodeStyle`
-[ ] Import the style file from wherever you downloaded it.

### Running Google format
#### IntelliJ
use the following key commands in any file you want to run it:
Mac: option + command + L
Windows: ctrl + alt + L 

#### Gradle
-[ ] in terminal run the following command:`./gradlew build`

if you see someting like this:
```
FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':spotlessJava'.
> The following files had format violations:
      src/main/java/io/integral/gradle/SampleApplication.java
          @@ -5,7 +5,7 @@
...
```
-[ ] in terminal run the following command:` ./gradlew spotlessApply`

as long as that was your only issue you, you should see something like this:
```
BUILD SUCCESSFUL in 1s
1 actionable task: 1 executed
```

# Current Research For unresolved items


[PostgreSQL/Spring configuration](https://jdbc.postgresql.org/documentation/head/connect.html)