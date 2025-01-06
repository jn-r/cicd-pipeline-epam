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
        script {
          docker.build("zh3008/pipeline:${env.BUILD_NUMBER}")
        }

      }
    }

    stage('Docker-push') {
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'docker_hub_creds_id') {
            def app = docker.image("zh3008/pipeline:${env.BUILD_NUMBER}")
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")}

          }

        }
      }

    }
  }