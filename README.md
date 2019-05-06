# JaCoCo

## Resources
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

[PostgreSQL/Spring configuration](https://jdbc.postgresql.org/documentation/head/connect.html)