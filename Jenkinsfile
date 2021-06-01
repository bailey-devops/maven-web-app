pipeline {
    
    agent any

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
              when {
              expression {
                currentBuild.result == null || currentBuild.result == 'SUCCESS' 
              }
            }
            steps {
                sh 'make publish'
            }
        }
      stage ('emailNotification') {
          steps {
              emailext body: 'Boa-web-app deployment information.', compressLog: true, subject: 'Boa-web-app depolyment', to: 'o.devops.bailey@gmail.com'
          }
        }
    }
}
