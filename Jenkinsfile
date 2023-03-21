pipeline {
  agent any

  stages {
    stage("Check Branches") {
      steps {
        script {
          // Branch가 master이면
          sh 'printenv'
        }
      }
    }
    stage("Send Email") {
      steps {
        script {
          echo "EMAIL"
        }
      }
    }
  }
}
