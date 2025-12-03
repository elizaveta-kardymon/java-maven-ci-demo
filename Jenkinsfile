pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                bat 'powershell -Command "mvn -B -U clean compile"'
            }
        }

        stage('Test') {
            steps {
                bat 'powershell -Command \"mvn -B test\"'
            }
        }

        stage('Package') {
            steps {
                bat 'powershell -Command \"mvn -B package\"'
            }
        }

        stage('Deploy (local)') {
            steps {
                echo 'Deploy skipped (local env)'
            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml'
        }
    }
}
