pipeline {
  agent none
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

    stage('Docker-push') {
      steps {
        script {
          withDockerRegistry(credentialsId: 'docker-hub-credentials-id', url: 'https://index.docker.io/v1/') {
            docker.image('zh3008/pipeline').push("latest")
            docker.image('zh3008/pipeline').push(env.BUILD_NUMBER)
          }
        }

      }
    }

  }
}