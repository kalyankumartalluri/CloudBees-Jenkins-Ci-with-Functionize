// Lets Run this From Github

pipeline {
    agent none
    stages {
          stage('Functionize-CLI') {
          environment {
          // 'This value is exported to all commands in this stage'
            PROJECT_DEPLOYMENT_ID = "321138d5f2159c974b704293e2701a3a"
            YOUR_API_KEY = "65c79f9961f6aec28539385fe77e639d"
            YOUR_SECRET_KEY = "16c8e1ade22c4ca3180121ded855c1b2"
          }
          agent {
              docker {
                image 'node:9.11.1'
                args  '-u root'
              }
          }
            steps {
              sh 'echo from Command $PROJECT_DEPLOYMENT_ID'
              sh 'echo from Command $YOUR_API_KEY'
              sh 'echo from Command $YOUR_API_KEY'
              sh 'rm -rf functionizecli'
              sh 'git clone https://functionize@bitbucket.org/functionize/functionizecli.git'
              sh 'cd functionizecli && npm install'
              sh 'cd functionizecli && npm install -g'
              sh 'cd functionizecli && wget -O - https://bitbucket.org/functionize/functionizecli/raw/master/ThirdParty_run.sh | bash'
            }
        }
    }
  }
