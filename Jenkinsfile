node {
  stage('SCM') {
    https://github.com/graj1/gradle-simple.git
  }
  stage('SonarQube Analysis') {
    withSonarQubeEnv() {
      sh "./gradlew sonarqube"
    }
  }
}
