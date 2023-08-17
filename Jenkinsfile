pipeline {
  agent any
  stages {
    // stage("Clone") {
    //     steps {        
    //         git 'https://github.com/akiramix1102/jenkin-test.git'
    //     }
    // }	  
   stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
  }
}
