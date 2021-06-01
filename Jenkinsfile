pipeline {
    
    agent any

    def mavenHome = tool name: "maven"
    
    stages {
      stage ('getCode') {
          steps {
        git 'https://github.com/bailey-devops/maven-web-app'
          }
      }
      stage ('mavenBuild') {
          steps {
              sh "${mavenHome}/bin/mvn clean package"
          }
      }
    }
}
