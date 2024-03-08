pipeline {
    agent any

    stages {
        stage('Build') {
            sh 'mvn clean install'
            echo 'Build successful!'
        }
        stage('Test') {
            sh 'mvn test'
            echo 'Tests successful!'
            post {
                junit 'target/surefire-reports/*.xml'
            }
        }
        stage('Deploy') {
            sh 'mvn deploy'
            echo 'Deployment successful!'
        }
    }

    post {
        failure {
            echo 'Pipeline failed!'
        }
    }
}
