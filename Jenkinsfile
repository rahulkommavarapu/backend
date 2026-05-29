pipeline {
    agent {label 'AGENT'}
    environment {
        PROJECT = 'expense'
        COMPONENT = 'backend'
        appVersion = ''
    }
    options {
        disableConcurrentBuilds()
        timeout(time: 30, unit: 'MINUTES')
    }

    stages {
        stage ('Read version') {
            steps {
                script{
                    sh 'pwd' sh 'ls -la' sh 'cat package.json'
                    
                    def packageJson = readJSON file: 'package.json'
                    appVersion = packageJson.version
                    echo "Version is: $appVersion"
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