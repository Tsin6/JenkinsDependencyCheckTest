pipeline {
    agent any
    stages {
        stage ('Checkout') {
            steps {
            git 'https://github.com/Tsin6/JenkinsDependencyCheckTest'
            }
        }
    
    stage('Code Quality Check via SonarQube') {
        steps {
            script {
            def scannerHome = tool 'SonarQube';
            withSonarQubeEnv('SonarQube') {
            sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=3X01_testing -Dsonar.sources=."
            }
            }
        }
    }
    }
    post {
        always {
            recordIssues enabledForFailure: true, tool: sonarQube()
        }
    }
}
