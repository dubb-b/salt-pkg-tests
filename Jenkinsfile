pipeline {
  agent {
    docker {
      image 'centos:6.9'
    }
    
  }
  stages {
    stage('CentOS6') {
      steps {
        echo 'Getting ENV Vars'
      }
    }
    stage('CentOS6 Run Tests') {
      steps {
        echo 'Running Tests'
      }
    }
    stage('CentOS6 Return Results') {
      steps {
        echo 'returning results'
      }
    }
  }
}