pipeline {
  agent {
    docker {
      image 'docker:24.0.2-cli'  // Alpine-based Docker image with CLI
      args '-v /var/run/docker.sock:/var/run/docker.sock'
    }
  }

  environment {
    DOCKER_IMAGE = "ahmedrafat/myapp"
    DOCKER_TAG = "${BUILD_NUMBER}"
  }

  stages {
    

    stage('Build Docker Image') {
      steps {
        sh '''
          docker build -t $DOCKER_IMAGE:$DOCKER_TAG .
        '''
      }
    }

    stage('Login to DockerHub') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
          sh '''
            echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin
          '''
        }
      }
    }

    stage('Push Docker Image') {
      steps {
        sh '''
          docker push $DOCKER_IMAGE:$DOCKER_TAG
        '''
      }
    }
  }

  post {
    success {
      echo " Docker image $DOCKER_IMAGE:$DOCKER_TAG pushed successfully."
    }
    failure {
      echo "Build or push failed."
    }
  }
}

