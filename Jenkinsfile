pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Rektyy2004/devops-petclinic.git'
            }
        }

        stage('Build') {
            steps {
                // Use Gradle here instead of Maven
                sh './gradlew clean build'
            }
        }

        stage('Test') {
            steps {
                sh './gradlew test'
            }
        }

        stage('SonarQube Analysis') {
            environment {
                SONARQUBE = credentials('sonarqube-token') // Optional if using token
            }
            steps {
                sh './gradlew sonarqube'
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: 'build/libs/*.jar', fingerprint: true
        }
        failure {
            echo 'Build failed!'
        }
    }
}
