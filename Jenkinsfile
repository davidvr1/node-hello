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

  }
}