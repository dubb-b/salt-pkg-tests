pipeline {
 agent any
 environment {

  STAGE1 = "CentOS 6"
  STAGE2 = 'CentOS 7'
  STAGE3 = 'Ubuntu 14.04'
  STAGE4 = 'Ubuntu 16.04'
  STAGE5 = 'Amazon Linux 2016.9'
  STAGE6 = 'Debian 7'
  STAGE7 = 'Debain 8'

 }

 stages {
  stage('CentOS 6') {
   agent {
    docker 'centos:6.9'
   }

   steps {
    notifyInformation("Starting the build....")
    sh 'hostname -I'

   }

  }

  stage('CentOS 7') {
   agent {
    docker 'centos:7.3.1611'
   }

   steps {
    notifyInformation("Starting the build....")
    sh 'hostname -I'

   }

  }
  stage('Ubuntu 14.04') {
   agent {
    docker 'ubuntu:14.04'
   }

   steps {
    notifyInformation("Starting the build....")
    sh 'hostname -I'

   }

  }
  stage('Ubuntu 16.04') {
   agent {
    docker 'ubuntu:16.04'
   }

   steps {
    notifyInformation("Starting the build....")
    sh 'cat /etc/hosts'

   }

  }
  stage('Amazon Linux 2016.09') {
   agent {
    docker 'amazonlinux:2016.09'
   }

   steps {
    notifyInformation("Starting the build....")
    sh 'cat /etc/hosts'

   }

  }

 }
}






def notifyStarted(String stageName) {
 // send to Slack
 slackSend(color: '#FFFF00', message: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})" + "\n  Stage -- " + stageName)
}

def notifySuccessful(String stageName) {
 slackSend(color: '#00FF00', message: "SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})" + "\n  Stage -- " + stageName)
}

def notifyFailed(String stageName) {
 slackSend(color: '#FF0000', message: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})" + "\n  Stage -- " + stageName)
}

def notifyInformation(String stageName) {
 slackSend(color: '#0000FF', message: "This is some random information about the build...." + "\n  Stage -- " + stageName)
}
