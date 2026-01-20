pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/sadish2006/two-tier-application.git'
            }
        }
        stage('Deploy Two-Tier App') {
            steps {
                sh '''
                docker-compose down || true
                docker-compose up --build
                '''
            }
        }
    }
}
