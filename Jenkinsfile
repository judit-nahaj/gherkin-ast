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
                fail {
                    emailext body: 'Hello', subject: 'Idea Pool Email Notif', to: 'judit_nahaj@epam.com'
                }
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