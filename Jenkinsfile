pipeline {
    //testing webhook for freestyle
    agent {
        label 'mavenHome'
        }

    stages {
      stage ('getCode') {
          steps {
        git 'https://github.com/bailey-devops/maven-web-app'
          }
      }
      stage ('mavenBuild') {
          steps {
              sh "/opt/maven/bin/mvn clean package"
          }
      }
      stage ('codeQuality') {
          steps {
              sh "/opt/maven/bin/mvn sonar:sonar"
          }
        }
      stage ('nexusRepo') {
          steps {
              sh "/opt/maven/bin/mvn deploy"
          }
        }
      stage ('tomcatDeployment') {
          steps {
                sh "scp -o StrictHostKeyChecking=no target/maven-web-app.war  ec2-user@3.234.225.159:/opt/tomcat9/webapps/" 
          }
        }
      stage ('emailNotification') {
          steps {
              emailext body: 'Boa-web-app deployment information.', compressLog: true, subject: 'Boa-web-app depolyment', to: 'o.devops.bailey@gmail.com'
          }
        }
    }
}
