pipeline {
  agent {
    node {
      label 'Slaves'
    }

  }
  stages {
    stage('SCM') {
      steps {
        build 'Pipeline'
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