pipeline {
    agent {label 'AGENT'}
    environment {
        PROJECT = 'expense'
        COMPONENT = 'backend'
        appVersion = ''
        ACC_ID  = '631164543894'
    }
    options {
        disableConcurrentBuilds()
        timeout(time: 30, unit: 'MINUTES')
    }

    stages {
        stage ('Read Version') {
            steps {
                script {

                    def packageJson = readJSON file: 'package.json'
                    appVersion = packageJson.version
                    echo "Version is: ${appVersion}"
                }
            }
        } 
        stage ('Install Dependencies') {
            steps {
                script {
                       sh """
                           npm install
                               """
                }
            }
        } 
        stage ('Docker Build') {
            steps {
                script {
                       sh """
                       aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin ${ACC_ID}.dkr.ecr.us-east-1.amazonaws.com
                               """
                }
            }
        }
    }
    post {
        always {
            echo 'I will always say Hello again'
            deleteDir()
        }
        failure {
            echo 'I will run when pipeline is failed'
        }
        success {
            echo 'I will run when pipeline is success'
        }
    }
}




















