pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/Niruifedi/demo-app.git'
            }
        }
        stage('Code Analysis') {
            environment {
                scannerHome = tool name: 'sonar'
            }
            steps {
                script {
                    withSonarQubeEnv('sonar') {
                        sh """
                            ${scannerHome}/bin/sonar-scanner \
                                -Dsonar.projectKey=CSN \
                                -Dsonar.projectName=CSN \
                                -Dsonar.sources=.
                        """
                    }
                }
            }
        }
    }
}
