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
                sh 'mvn clean verify'
                echo 'Build with Maven'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
                echo 'Test Analysis'
            }
        }
        
        stage('Deploy to Environments') {
            parallel {
            stage('Deploy to Application Server') {
                steps {
                    deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://3.144.187.92:8080')], contextPath: 'webapps', war: '**/*.war'
            }
        }
            stage('Deploy to Artifacts') {
                steps {
                    echo 'Deploy to Tomcat-1'
            }
        }
            stage('User Acceptance Server') {
                steps {
                    echo 'Deploy to Tomcat-2'
            }
        }
  }
}

    }
}


