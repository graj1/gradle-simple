node {
  stage('SCM') {
    checkout scm
  }
  stage('Build') {
      steps {
        sh './gradlew clean build'
      }
    }
  stage('SonarQube Analysis') {
    withSonarQubeEnv('sonarqube') {
      sh "./gradlew sonarqube"
    }
  }
}

