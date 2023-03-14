pipeline {
  agent {
    node {
      label 'Slaves'
    }

  }
  stages {
    stage('SCM') {
      steps {
        git(url: 'https://github.com/kssreddy1/paytmwar.git', branch: 'master')
      }
    }

  }
}