def notifyStarted(String stageName) {
  // send to Slack
  slackSend (color: '#FFFF00', message: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})" + "\n  Stage -- " + stageName)

  // send to email
  emailext (
      subject: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
      body: """<p>STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
        <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>&QUOT;</p>""",
      recipientProviders: [[$class: 'DevelopersRecipientProvider']]
    )
}

def notifySuccessful(String stageName) {
  slackSend (color: '#00FF00', message: "SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})" + "\n  Stage -- " + stageName)

  emailext (
      subject: "SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
      body: """<p>SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
        <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>&QUOT;</p>""",
      recipientProviders: [[$class: 'DevelopersRecipientProvider']]
    )
}

def notifyFailed(String stageName) {
  slackSend (color: '#FF0000', message: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})" + "\n  Stage -- " + stageName)

  emailext (
      subject: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
      body: """<p>FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
        <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>&QUOT;</p>""",
      recipientProviders: [[$class: 'DevelopersRecipientProvider']]
    )
}

def notifyInformation(String stageName) {
  slackSend (color: '#0000FF', message: "This is some random information about the build...." + "\n  Stage -- " + stageName)
}


pipeline {
	agent none
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
           stage('CentOS 6') 
            {
            	agent { docker 'centos:6.9' }          
                steps 
                  {
                    notifyInformation("Starting the build....")
                    sh 'hostname -I'   
               
                  }   
                  
                post
                  {
                    success
                    {
                      notifySuccessful("$STAGE1")
                    }
                    failure
                    {
                      notifyFailed("$STAGE1")
                    }

                  }
                
            }

           stage('CentOS 7') 
            {
            	agent { docker 'centos:7.3.1611' }
                steps 
                  {
                      notifyStarted("$STAGE2")
                      notifyInformation("Starting the build....")
                      sh 'hostname -I'      

                  }
                 post
                  {
                    success
                    {
                      notifySuccessful("$STAGE2")
                    }
                    failure
                    {
                      notifyFailed("$STAGE2")
                    }

                  }            
            }
           stage('Ubuntu 14.04')  
            {
            	agent { docker 'ubuntu:14.04' }
                steps 
                  {
                      notifyStarted("$STAGE3")
                      notifyInformation("Starting the build....")
                      sh 'hostname -I'   
    
                  }
                post
                  {
                    success
                    {
                      notifySuccessful("$STAGE3")
                    }
                    failure
                    {
                      notifyFailed("$STAGE3")
                    }

                  }    
                
            }
            stage('Ubuntu 16.04')  
            {
            	agent { docker 'ubuntu:16.04' }
                steps 
                  {
                      notifyStarted("$STAGE4")
                      notifyInformation("Starting the build....")
                      sh 'hostname -I'   
  
                  } 
                post
                  {
                    success
                    {
                      notifySuccessful("$STAGE4")
                    }
                    failure
                    {
                      notifyFailed("$STAGE4")
                    }

                  }
            }
            stage('Amazon Linux 2016.09')  
            {
            	agent { docker 'amazonlinux:2016.09' }
                steps 
                  {
                      notifyStarted("$STAGE5")
                      notifyInformation("Starting the build....")
                      sh 'cat /etc/hosts'   
  
                  } 
                post
                  {
                    success
                    {
                      notifySuccessful("$STAGE5")
                    }
                    failure
                    {
                      notifyFailed("$STAGE5")
                    }

                  }
            }
        }
}
