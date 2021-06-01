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
        buildInfo = rtMaven.run pom: 'maven-web-app/pom.xml', goals: 'clean package'
          }
      }
    }
}
