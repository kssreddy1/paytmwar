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

    stage('BUILD') {
      steps {
        sh '/usr/share/maven/bin/mvn clean package'
      }
    }

    stage('QA') {
      steps {
        sh '/usr/share/maven/bin/mvn sonar:sonar'
      }
    }

  }
}