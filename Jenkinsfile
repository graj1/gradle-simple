node {
  stage('SCM') {
    checkout scm
  }
  
stage('SonarQube analysis') {
    def scannerHome = tool name: 'sonar_scanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation';
    withSonarQubeEnv('SonarQube') { 
      sh "${scannerHome}/bin/sonar-scanner"
      def scannerOpts = "-Dsonar.projectKey=rms-gateway -Dsonar.projectName=rms-gateway -Dsonar.projectVersion=1.0"
    }
  }
}

