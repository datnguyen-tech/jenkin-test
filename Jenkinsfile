pipeline {

  agent any
  environment {
    DOCKER_IMAGE = "datnguyen7031/jenkin-test"
    DOCKER_TAG="${GIT_BRANCH.tokenize('/').pop()}-${GIT_COMMIT.substring(0,7)}"
  }

  stages {
    stage("test") {
        steps {
            echo "Testing...."
          }
      }

    stage("build") {
            
        steps {
          
        echo DOCKER_IMAGE
        echo DOCKER_TAG

        withDockerRegistry(credentialsId: 'docker-hub	', url: 'https://index.docker.io/v1/') {
            
            sh "docker build -t ${DOCKER_IMAGE}:${DOCKER_TAG} . "
            sh "docker tag ${DOCKER_IMAGE}:${DOCKER_TAG} ${DOCKER_IMAGE}:latest"
            sh "docker push ${DOCKER_IMAGE}:${DOCKER_TAG}"
            sh "docker push ${DOCKER_IMAGE}:latest"

        }    

            //clean to save disk
            sh "docker image rm -f ${DOCKER_IMAGE}:${DOCKER_TAG}"
            sh "docker image rm -f ${DOCKER_IMAGE}:latest"
            sh "docker image prune -f"

        }

    }
	  


  }

}