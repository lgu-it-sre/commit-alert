pipeline {
  agent any

  stages {
    stage("Check Diff") {
      steps {
        script {
          checkout scmGit(
            branches: [[name: 'develop']],
            userRemoteConfigs: [[
              credentialsId: 'lgu-it-sre',
              url: 'https://github.com/lgu-it-sre/jenkins-shared-lib.git'
            ]]
          )
          diff = sh(script: "git diff ${env.before}..${env.after}", returnStdout: true)
        }
      }
    }
    stage("Send Email") {
      steps {
        script {
          html = diff.replaceAll('\n', '<br>').replaceAll(' ', '&nbsp;')
          emailext(
            subject: "SI JENKINS-NUCUBE-LIB 변경사항",
            body: "<pre>${html}</pre>",
            to: recipients.join(','),
            from: 'noreply@mail.com'
          )
        }
      }
    }
  }
}
