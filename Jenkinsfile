node {

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('Build') {
      steps {
        sh './gradlew clean build'
      }
    }
    stage('SonarQube analysis') {
      steps {
        withSonarQubeEnv('SonarQube') {
          sh "${scannerHome}/bin/sonar-scanner"
        }
      }
    }
  }
}
}

