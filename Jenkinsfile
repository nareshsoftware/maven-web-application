node{
    build name 'Dev - ${Build_Number}'
    echo "the node name is : ${env.Node_Name}"
     echo "the job name is : ${env.Job_Name}"
     echo "the build number is : ${Build_Number}"
   properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([cron('* * * * *'), pollSCM('* * * * *')])])
    timestamps {
 }
    def mavenHome = tool name: "maven3.8.5" 
stage('checkoutcode'){
git branch: 'development', credentialsId: 'e9bced31-9073-478b-b261-b04b90f1355c', url: 'https://github.com/nareshsoftware/maven-web-application.git'
}
stage('build'){
    sh "$mavenHome/bin/mvn clean package"
}
/* stage('sonarqube'){
    sh "$mavenHome/bin/mvn sonar:sonar"
}
stage('artifactstonexus'){
    sh "$mavenHome/bin/mvn deploy"
}
stage('deplottotomcat'){
sshagent(['133b6392-6c7e-48ba-9b9a-68b16f7c3ad8']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.126.209.223:/opt/apache-tomcat-9.0.62/webapps/"
}
} */
}
