pipeline {
    
    agent { label 'agent1-maven' }

    stages {
      stage ('getCode') {
        git 'https://github.com/bailey-devops/maven-web-app'
      }
      stage ('mavenBuild') {
        sh 'mvn clean package'
      }
    }
}
