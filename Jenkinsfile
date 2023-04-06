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
    stage("Push into JFROG") {
      steps {
      sh 'curl -u $JFROG_USER:$JFROG_PWD -T target/hello-world-0.1.0.jar "https://rudradevops.jfrog.io/artifactory/maven-demo/$BUILD_NUMBER/hello-world-0.1.0.jar"'
      }
    }
    stage("Deploy into server") {
      steps {
        script {
        def remote = [:]
      remote.name = 'myapp_server'
      remote.host = '172.31.15.41'
      remote.user = $APP_USER
      remote.password = $APP_PWD
      remote.allowAnyHosts = true
      sshCommand remote: remote, command: "ls -lrt"
      sshCommand remote: remote, command: "for i in {1..5}; do echo -n \"Loop \$i \"; date ; sleep 1; done"
    }
      }
    }
  }
}
  
