pipeline {
    agent { docker 'themattrix/tox' }
    stages {
        stage("Build") {
            steps {
                sh 'tox -c allure-pytest'
                sh 'tox -c allure-python-commons'
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
