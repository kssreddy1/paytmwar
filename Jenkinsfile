pipeline {
  agent {
    node {
      label 'Slaves'
    }

  }
  stages {
    stage('SCM') {
      steps {
        git(changelog: true, url: 'https://github.com/kssreddy1/paytmwar.git', branch: 'master', credentialsId: 'GitHub_Token')
      }
    }

  }
}