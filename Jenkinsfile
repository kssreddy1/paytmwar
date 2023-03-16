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

    stage('EMAIL') {
      steps {
        emailext(subject: 'Build Success Mai', body: 'this is regarding Build Success or failure mails', from: 'samba81424.sr@gmail.com', replyTo: 'samba81424.sr@gmail.com', to: 'samba81424.sr@gmail.com')
      }
    }

  }
}