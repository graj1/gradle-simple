node {
  stage('SCM') {
    checkout scm
  }
  
  stage('SonarQube Analysis') {
    withSonarQubeEnv('sonarqube') {
      sh "./gradlew sonarqube"
    }
  }
}

