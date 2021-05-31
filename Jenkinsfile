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
                    junit 'coverage/clover.xml'
                    archiveArtifacts 'coverage/clover.xml'
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