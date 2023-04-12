node {
  stage('SCM') {
    git 'https://github.com/graj1/gradle-simple'
  }
  stage('SonarQube Analysis') {
    withSonarQubeEnv() {
      sh "./gradlew sonarqube"
    }
  }
}
