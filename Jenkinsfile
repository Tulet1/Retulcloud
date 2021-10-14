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
        
        stage('Code Quality Scan') {
            steps {
                withSonarQubeEnv('sonar') {
                    sh "mvn -f webapp/pom.xml sonar:sonar"
                }
            }
        }
                    
        stage('Deploy to Server') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://3.144.187.92:8080')], contextPath: 'webapps', war: '**/*.war'
            }
        }

    }
}


