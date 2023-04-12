stage('Sonarqube') {
    environment {
        scannerHome = tool 'SonarQubeScanner'
    }
    steps {
        withSonarQubeEnv('sonarqube') {
            sh "${scannerHome}/bin/sonar-scanner"
            -Dsonar.projectKey=rms-gateway \
            -Dsonar.host.url=http://20.124.136.37 \
            -Dsonar.login=sqp_fdaf586de616395c2db58177f6a4defb0421bad9
        }
        timeout(time: 10, unit: 'MINUTES') {
            waitForQualityGate abortPipeline: true
        }
    }
}
