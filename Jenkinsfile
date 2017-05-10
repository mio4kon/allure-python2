pipeline {
    agent { docker 'themattrix/tox' }
    stages {
        stage("Build") {
            steps {
                sh 'tox -c allure-python-commons/tox.ini'
                sh 'tox -c allure-pytest/tox.ini'
            }
        }
    }
}
