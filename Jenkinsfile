pipeline {
    agent any
    tools {
        dockerTool 'docker'
        maven 'maven'
        gradle 'gradle'
    }
    stages {
        stage('Checkout'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], 
                doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], 
                userRemoteConfigs: [[credentialsId: 'github-pvt-repo-token', url: 'https://github.com/rajat132/node-slave-test.git']]])
            }
        }
        stage('Build'){
            steps{
                sh "mvn --version"
                //sh "mvn clean install"
                sh "mvn clean package"
                //sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
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