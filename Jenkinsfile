pipeline {
    agent any
    tools {
            maven 'Maven3'  // Ensure Maven is installed
            jdk 'Java_Home'     // Ensure JDK is installed
        }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/GeorgeChirikov/timeCalculator.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Code Coverage') {
            steps {
                jacoco execPattern: '**/target/jacoco.exec'
            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml'
            jacoco execPattern: '**/target/jacoco.exec'
        }
    }
}

