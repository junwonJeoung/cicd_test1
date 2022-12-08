pipeline {
  agent { label "jenkins-node" }

  triggers {
    pollSCM('* * * * *')
  }

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', 
        url: 'https://github.com/junwonJeoung/cicd_test1.git'
      }
    }
    stage('Build') {
      steps {
        sh 'mvn clean package -DskipTest=true'
      }
    }
    stage('Test') {
      steps {
        sh 'mvn test'
      }
    }
    stage('Deploy') {
      steps {
        deploy adapters: [tomcat9(credentialsId: 'tomcat-mainger', url: 'https://github.com/junwonJeoung/cicd_test1.git')], contextPath: null, war: 'target/hello-world.war'
      }
    }
  }
}

