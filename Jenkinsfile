pipeline {
  agent {
    node {
      label 'docker-slave'
    }

  }
  stages {
    stage('Checkout code') {
      steps {
        git(url: 'https://github.com/davidvr1/node-hello.git', branch: 'master', changelog: true, poll: true, credentialsId: 'github')
      }
    }

    stage('Build docker image') {
      steps {
        sh 'docker build . -t node-hello:$BUILD_ID'
      }
    }

    stage('push docker image') {
      steps {
        withDockerRegistry(credentialsId: 'docker-hub-creds', url: 'https://index.docker.io/v1/') {
          sh 'docker tag node-hello:$BUILD_ID varshoer/node-hello:$BUILD_ID && docker push varshoer/node-hello:$BUILD_ID'
        }

      }
    }

  }
}