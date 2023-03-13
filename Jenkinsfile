pipeline {
  agent {
    node {
      label 'Slaves'
    }

  }
  stages {
    stage('SCM') {
      steps {
        build 'PIPE'
      }
    }

    stage('BUILD') {
      steps {
        sh '/usr/share/maven/bin/mvn clean package'
      }
    }

  }
  environment {
    MAVEN_OPTS = ''
  }
}