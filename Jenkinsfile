pipeline {
    
    agent { label 'agent1-maven' }

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
