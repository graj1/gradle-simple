node {
    stage 'Checkout'

    checkout scm

    stage 'Gradle Static Analysis'
    withSonarQubeEnv {
        sh "./gradlew clean sonarqube"
    }

    stage 'Maven Static Analysis'
    withSonarQubeEnv {
        sh "./mvnw -Pcoverage-per-test clean org.jacoco:jacoco-maven-plugin:prepare-agent install sonar:sonar"
    }
}
