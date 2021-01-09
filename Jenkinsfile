pipeline {
    agent none
    stages {
        stage('Build'){
            agent {
                label 'slave1'
            }
            steps{
                checkout scm
                sh "mvn compile"
            }
            post{
                always{
                    cleanWs()
                }
            }
        }
        stage('Test') {
            agent {
                label 'slave2'
            }
            steps {
                sh 'mvn test'
            }
            post{
                always{
                    cleanWs()
                }
            }
        }
    }
}