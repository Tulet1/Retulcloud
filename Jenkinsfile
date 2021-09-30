pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                git 'https://github.com/seeewhy/DevOpsBasics.git'
                echo 'cloning git repo'
            }
        }
        stage('Test') {
            steps {
                sh 'test'
                echo 'Test Analysis'
            }
        }
        stage('Build') {
            steps {
                sh 'test install package'
                echo 'Build with Maven'
            }
        }
        stage('Deploy to Server') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://52.14.207.173:8080')], contextPath: 'webapps', war: '**/*.war'
            }
        }


    }
}

