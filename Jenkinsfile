pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/inamulhasankiaq-devops/Demo_proj.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh '''
                        sonar-scanner \
                        -Dsonar.projectKey=sonarqube_proj_inam \
                        -Dsonar.projectName=sonarqube_proj_inam \
                        -Dsonar.sources=.
                    '''
                }
            }
        }
    }
}
