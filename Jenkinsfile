node{

def maven = tool name: "latest"

echo "node running name: ${env.NODE_NAME} "

echo "job name:  ${env.JOB_NAME} "

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '5', numToKeepStr: '5'))])
properties([pipelineTriggers([pollSCM('* * * * *')])])

buildName 'Dev - ${BUILD_NUMBER}'

buildDescription 'this is for testing pipeline for oct batch'

//checkout stage
stage('checkout'){

  git 'https://github.com/sanchitraj5/maven-java-oct.git'
}
//build stage
stage('building'){
sh "$maven/bin/mvn clean package"
/*
//sonarqube report
stage ('sonarqubereport'){
sh "$maven/bin/mvn sonar:sonar"
}


//upload nexus
stage ('nexus upload'){
sh "$maven/bin/mvn deploy"
}
*/

}
}//Node closing
