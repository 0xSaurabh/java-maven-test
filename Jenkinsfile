pipeline {

    agent any

    tools {
        maven 'maven-latest'
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/0xSaurabh/java-maven-test.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                sh 'mvn sonar:sonar'
            }
        }

        stage('Deploy to Nexus') {
            steps {
                sh 'mvn deploy'
            }
        }

    }
}
