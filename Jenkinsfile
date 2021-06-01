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
    }
}
