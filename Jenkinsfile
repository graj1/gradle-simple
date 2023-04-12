pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build and Test') {
            steps {
                sh './gradlew build'
            }
        }
        
        stage('Code Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh './gradlew sonarqube'
                }
            }
        }
    }
    
    post {
        always {
            junit 'build/test-results/**/*.xml'
            archiveArtifacts 'build/libs/*.jar'
        }
        
        success {
            script {
                def qualityGate = waitForQualityGate()
                if (qualityGate.status != 'OK') {
                    error "Pipeline failed due to quality gate failure: ${qualityGate.status}"
                }
            }
        }
    }
}
