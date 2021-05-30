pipeline {
    agent any

    stages {
        stage ('Build & Test') {
            steps {
                sh '''
                npm i
                npm test
                '''
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}