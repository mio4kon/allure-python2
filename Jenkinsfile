pipeline {
    agent { docker 'themattrix/tox' }
    stages {
        stage("Build") {
            steps {
                dir('allure-pytest') {
                    sh 'pwd'
                }
                dir('allure-python-commons') {
                    sh 'pwd'
                }
            }
        }
    }
    post {
        failure {
            slackSend message: "${env.JOB_NAME} - #${env.BUILD_NUMBER} failed (<${env.BUILD_URL}|Open>)",
                    color: 'danger', teamDomain: 'qameta', channel: 'allure', tokenCredentialId: 'allure-channel'
        }
    }
}
