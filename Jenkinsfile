pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'script ./scripts/build.sh'
      }
    }

    stage('Test') {
      steps {
        sh 'script ./scripts/test.sh'
      }
    }

    stage('Docker-build') {
      steps {
        sh 'docker build -t zh3008/pipeline .'
      }
    }

  }
}