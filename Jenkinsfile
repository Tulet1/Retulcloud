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
                deploy adapters: [tomcat9(credentialsId: 'Tomcat_keys', path: '', url: 'http://3.144.216.115:8080/')], contextPath: 'webapp', war: '**/*.war'
            }
        }
        stage('Deploy to QA') {
            steps {
                echo 'Deploy to Tomcat'
            }
        }        
              
            
    }
}


