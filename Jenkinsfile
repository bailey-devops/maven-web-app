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
              environment {
            MVN_COMMAND = "mvn clean package"
              }
          }
      }
    }
}
