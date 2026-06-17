pipeline {
    agent any
    environment {
        name = 'sumedh'
    }
    parameters{
        string (name: 'person', defaultValue: 'unnati development', description: 'Who are you?')
        booleanParam(name: 'isMale', defaultValue: true, description: '')
        choice(name: 'city', choices: ['jaipur','mumbai','pune'], description: '')
    }
    stages {
        stage('Run a Command') {
            steps {
                sh 'date'
                sh 'ls'
                sh 'pwd'
            }
        }
        stage('Environment Variable') {
            environment {
                username = 'myusername'
            }
            steps {
                sh 'echo "${BUILD_ID}"'
                sh 'echo "${name}"'
                sh 'echo "${username}"'
            }
        }
        stage('Parameters') {
            steps {
                echo 'Deploy on test1'
                sh 'echo "${name}"'
                sh 'echo "${person}"' 
            }
        }
        stage('Continue ?') {
            input {
                message 'Should We Continue ?'
                ok "Yes We should"
            }
                
            steps {
                echo 'Deploy on prod1'
            }
        }
        stage('Deploy on prod') {
            steps {
                echo 'Deploy on prod1'
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
        failure {
            echo 'failure !'
        }
        success {
            echo 'success !'
        }
    }
}
