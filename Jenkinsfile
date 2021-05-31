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
            post {
                always {
                    junit 'reports/junit.xml'
                    archiveArtifacts 'reports/junit.xml'
                }
            }
        }
        stage ('Release') {
            steps {
                echo 'code here'
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}