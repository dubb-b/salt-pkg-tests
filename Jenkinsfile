pipeline {
  agent {
    docker {
      image 'centos:6.9'
    }
    
  }
  stages {
    stage('CentOS6') {
      steps {
        sh 'hostname -I'
        echo 'Getting Env Vars'
        echo 'Running Package Tests'
      }
    }
    stage('CentOS7') {
      steps {
        sh 'hostname -I'
      }
    }
    stage('Ubuntu 14.04') {
      steps {
        sh 'hostname -I'
      }
    }
    stage('Ubuntu 16.04') {
      steps {
        sh 'hostname -I'
      }
    }
  }
}