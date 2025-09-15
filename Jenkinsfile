pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Faiz0603/pro1.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
        stage('Deploy') {
            steps {
                
                   sh 'scp target/*.jar user@remote-server:/path/to/deploy'
                   sh 'docker build -t my-spring-boot-app .'
                   sh 'docker push my-spring-boot-app'
            }
        }
    }
}




