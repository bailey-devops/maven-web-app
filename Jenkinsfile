node
 {
  //tool name: "maven 3.8.1"
  def mavenHome = "/opt/maven"
  /*
      echo "GitHub BranhName ${env.BRANCH_NAME}"
      echo "Jenkins Job Number ${env.BUILD_NUMBER}"
      echo "Jenkins Node Name ${env.NODE_NAME}"
  
      echo "Jenkins Home ${env.JENKINS_HOME}"
      echo "Jenkins URL ${env.JENKINS_URL}"
      echo "JOB Name ${env.JOB_NAME}"
  
   properties([[$class: 'JiraProjectProperty'], buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '2', daysToKeepStr: '', numToKeepStr: '2')), pipelineTriggers([pollSCM('* * * * *')])])
  */
    stage("CheckOutCodeGit")
      {
      git 'https://github.com/bailey-devops/maven-web-app.git' 
      }
 
    stage("Build")
    {
    sh "${mavenHome}/bin/mvn clean package"
  }
 
    stage("ExecuteSonarQubeReport")
      {
 sh "${mavenHome}/bin/mvn sonar:sonar"
 }
 
 stage("UploadArtifactsintoNexus")
 {
 sh "${mavenHome}/bin/mvn deploy"
 }
 
  stage("DeployAppTomcat")
 {
  sshagent(['29d3ab89-1b7c-4187-80ff-8a5e9672a272']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war  ec2-user@3.234.225.159:/opt/tomcat9/webapps/" 
  }
 }
 
 stage('EmailNotification')
 {
 mail bcc: 'o.devops.bailey@gmail.com', body: '''Build is over

 Thanks,
 Landmart Tech,
 0000000000.''', cc: 'o.devops.bailey@gmail.com', from: '', replyTo: '', subject: 'Build is over!!', to: 'o.devops.bailey@gmail.com'
 }
 
 }
