pipeline {
agent any
  stages {
  stage("Chekout code") {
    steps {
    sh 'echo "Welcome to Jenkins"' 
      git 'https://github.com/dstar55/docker-hello-world-spring-boot.git'
    }
    }
    stage("Build") {
      steps {
      sh 'mvn clean install'
      }
    }
  }
}
  
