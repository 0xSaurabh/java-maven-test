pipeline {

    agent any

    tools {
        maven 'maven-latest'
    }

    stages {

        // Checkout stage
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/0xSaurabh/java-maven-test.git'
            }
        }

        // Build stage
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        // SonarQube analysis
        stage('SonarQube Analysis') {
            steps {
                sh 'mvn sonar:sonar'
            }
        }

        // Upload artifact to Nexus
        stage('Deploy to Nexus') {
            steps {
                sh 'mvn deploy'
            }
        }

    }
}
