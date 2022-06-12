pipeline {
  agent any
  tools {
    maven 'maven' 
  }
  stages {
    stage ('checkout') {
        steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/siva8091/hello-world.git']]])
        }
    }  
    stage ('Build') {
      steps {
          checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/siva8091/hello-world.git']]])
          sh 'mvn clean install'
      }
    }
    stage('Deploy') {
        steps {
            sshagent(['ubuntu']) {
                sh 'cp -R /home/ubuntu/workspace/TEST-3/target/hello-world.war /home/ubuntu/tomcat/apache-tomcat-10.0.22/webapps'
    // some block
            }
        }
    }
  }
}  
