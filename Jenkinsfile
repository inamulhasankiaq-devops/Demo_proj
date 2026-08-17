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
                def scannerHome = tool 'SonarScanner'
                withSonarQubeEnv('SonarQube') {
                    sh '''
                        ${scannerHome}/bin/sonar-scanner \
                        -Dsonar.projectKey=sonarqube_proj_inam \
                        -Dsonar.projectName=sonarqube_proj_inam \
                        -Dsonar.sources=. \
                        -Dsonar.host.url=http://localhost:9000 \
                        -Dsonar.login=sqp_bc087db9f15f69768cd42891edaca950f505dfb3
                    '''
                }
            }
        }
    }
}
