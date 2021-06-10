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
                    mail body: "Build & Test Stage Failure.\nDetails at ${env.BUILD_URL}", subject: 'Idea Pool Email Notif', to: "${env.RECIPIENTS}"
                }
                always {
                    junit 'reports/junit.xml'
                    archiveArtifacts 'reports/junit.xml'
                }
            }
        }
        stage ('Release') {
            steps {
                sh '''
                npm config set '//registry.npmjs.org/:_authToken' "${GITHUBTOKEN}"
                npm publish
                '''
            }
            post {
                success {
                    mail body: "Release Stage Success.\nDetails at ${env.BUILD_URL}", subject: 'Idea Pool Email Notif', to: "${env.RECIPIENTS}"
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