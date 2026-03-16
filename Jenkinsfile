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

        // Deploy to Tomcat
        stage('Deploy to Tomcat') {
            steps {
                sshagent(['aa814d68-d0e8-4d0b-b07d-5cb3c8e0fdd0']) {
                    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@15.206.89.91:/opt/apache-tomcat-9.0.115/webapps"
                }
            }
        }
/*
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
*/
    }
}
