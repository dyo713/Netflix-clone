pipeline {
    agent any
    
    stages {
        stage('Fetch Code') {
            steps {
                git 'https://github.com/dyo713/Netflix-clone.git'
            }
        }
        stage('Code Analysis') {
            environment {
                scannerHome = tool 'sonar-scanner'
            }
            steps {
                script {
                    withSonarQubeEnv('Sonar') {
                        sh "${scannerHome}/bin/sonar-scanner \
                            -Dsonar.projectKey=netflix \
                            -Dsonar.projectName=netflix \
                            -Dsonar.projectVersion=1.0 \
                            -Dsonar.sources=."
                    }
                }
            }
        }
    }
}