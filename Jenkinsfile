node {

    def mavenHome = tool name: 'maven-latest'

    echo "the node name is: --> ${env.NODE_NAME}"

    echo "the job name is: --> ${env.JOB_NAME}"

    echo "this build number is: --> ${env.BUILD_NUMBER}"

    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '5'))])

    // Checkout stage
    stage('Checkout Code') {
        git branch: 'main', url: 'https://github.com/0xSaurabh/java-maven-test.git'
    }

    // Build stage
    stage('Build') {
        sh "${mavenHome}/bin/mvn clean package"
    }
/*
    // SonarQube analysis
    stage('SonarQube Analysis') {
        sh "${mavenHome}/bin/mvn sonar:sonar"
    }

    // Upload artifact to Nexus
    stage('Upload to Nexus') {
        sh "${mavenHome}/bin/mvn deploy"
    }

    // Deploy to Tomcat
    stage('Deploy to Tomcat') {
        sshagent(['aa814d68-d0e8-4d0b-b07d-5cb3c8e0fdd0']) {
            sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@15.206.89.91:/opt/apache-tomcat-9.0.115/webapps"
        }
    }
*/
}
