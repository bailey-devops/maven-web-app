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
            sh 'mvn clean package'
          }
      }
    }
}
