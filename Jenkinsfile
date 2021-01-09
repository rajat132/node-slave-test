pipeline {
    agent none
    stages {
        stage('Build'){
            agent {
                label 'slave1'
            }
            steps{
                sh "mvn --version"
                sh "mvn clean package"
                stash includes: '**/target/*.jar', name: 'app'
            }
        }
        stage('Test') {
            agent {
                label 'slave2'
            }
            steps {
                unstash 'app'
                sh 'mvn test'
            }
        }
    }
    post{
        always{
            cleanWs()
        }
    }
}