pipeline{
  agent {
    docker {
      image 'node:8-alpine'
      args '-p 3000:3000'
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
    stage("Deliver"){
        steps{
            echo "====++++executing Deliver++++===="
            sh './jenkins/scripts/deliver.sh'
            input message: 'Finished using the web site? (Click "Proceed" to continue)'
            sh './jenkins/scripts/kill.sh'
        }
    }
  }
}
