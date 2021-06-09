pipeline {
    agent any

    stages {
        stage ("Build & Test") {
            steps {
                sh '''
                npm i
                npm test
                '''
            }
            post {
                failure {
                    mail body: "Build & Test Stage Failure.\nDetails at ${env.BUILD_URL}", subject: 'Idea Pool Email Notif', to: 'judit_nahaj@epam.com'
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
            post {
                success {
                    mail body: "Release Stage Success.\nDetails at ${env.BUILD_URL}", subject: 'Idea Pool Email Notif', to: 'judit_nahaj@epam.com'
                }
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}