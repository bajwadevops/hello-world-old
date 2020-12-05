pipeline {
  agent any
  stages {

    stage('Docker Build') {
      steps {
        sh 'docker build -t docker-hello-world:latest'
      }
    }
    stage('Docker Push') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'dockerhub_Pass', usernameVariable: 'dockerhub_User')]) {
          sh "docker login -u ${env.dockerhub_User} -p ${env.dockerhub_Pass}"
          sh 'docker push docker-hello-world:latest'
        }
      }
    }
  }
}
