pipeline{
  agent {
    docker {
      image 'node:8-alpine'
    }
  }
  environment {
    CI = 'true'
  }
  stages {
    stage("Build"){
        steps{
            echo "====++++executing Build++++===="
            sh 'npm install'
        }
    }
    stage("Test") {
        steps {
          sh './jenkins/scripts/test.sh'
        }
    }
  }
}
