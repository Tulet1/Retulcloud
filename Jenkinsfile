pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                git 'https://github.com/seeewhy/DevOpsBasics.git'
                echo 'cloning git repo'
            }
        }
        stage('Build') {
            steps {
                sh 'test install package'
                echo 'Build with Maven'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
                echo 'Test Analysis'
            }
        }
        stage('Deploy to Server') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://52.14.207.173:8080')], contextPath: 'webapps', war: '**/*.war'
            }
        }


    }
}


