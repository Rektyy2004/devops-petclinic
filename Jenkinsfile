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
                bat 'gradlew.bat clean build -x test'
            }
        }

        stage('Test') {
            steps {
                echo 'Tests skipped in pipeline'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                echo 'SonarQube skipped'
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: 'build/libs/*.jar', fingerprint: true
            echo 'Build successful!'
        }

        failure {
            echo 'Build failed!'
        }
    }
}
