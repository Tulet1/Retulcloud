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
                sh 'mvn clean package'
                echo 'Build with Maven'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
                echo 'Test Analysis'
            }
        }
        
                     
        stage('Deploy to Azure Server') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat-azure', path: '', url: 'http://20.121.64.12:8080/')], contextPath: 'webapp', war: '**/*.war'
            }
        }
        stage('Deploy to QA') {
            steps {
                echo 'Deploy to Tomcat'
            }
        }        
              
            
    }
}


