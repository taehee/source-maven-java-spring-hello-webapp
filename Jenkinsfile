pipeline {
  agent any

  triggers {
    pollSCM('* * * * *')
  }

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', 
        url: 'https://github.com/taehee/source-maven-java-spring-hello-webapp.git'
      }
    }
    stage('Build') {
      steps {
        sh 'mvn clean'
      }
    }
    stage('Test') {
      steps {
        sh 'mvn package'
      }
    }
    stage('Deploy') {
      steps {
        deploy adapters: [tomcat9(credentialsId: 'tomcat-manager', url: 'http://3.38.172.244:8080/')], contextPath: null, war: 'hello-world.war'
      }
    }
  }
}
