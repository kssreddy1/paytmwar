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

    stage('BUILD') {
      steps {
        sh '/usr/share/maven/bin/mvn clean package'
      }
    }

    stage('QA') {
      steps {
        withSonarQubeEnv(installationName: 'sonar', credentialsId: 'sonar_token', envOnly: true) {
          sh '/usr/share/maven/bin/mvn sonar:sonar'
        }

      }
    }

    stage('Deploy') {
      steps {
        sh '/usr/share/maven/bin/mvn deploy'
      }
    }

    stage('Deploy Artifacts Into Tomcat') {
      steps {
        sh 'scp /home/ubuntu/jenkins/workspace/paytmwar_master/target/test-bus.war 15.207.222.96:/opt/tomcat9/webapps'
      }
    }

    stage('') {
      steps {
        emailext(subject: 'Build ', body: 'This is regarding Build Success or Failure Information purpose', from: 'samba81424.sr@gmail.com', replyTo: 'samba81424.sr@gmail.comsamba81424.sr@gmail.com', to: 'samba81424.sr@gmail.com')
      }
    }

  }
}