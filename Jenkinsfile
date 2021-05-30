pipeline {
    agent any

    stages {
        stage ('Build & Test') {
            steps {
                script '''
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