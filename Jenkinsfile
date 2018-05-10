// Lets Run this From Github

pipeline {
    agent none
    stages {
        stage('lint-css') {
          agent {
              docker {
                image 'node:9.11.1'
                args  '-u root'
              }
          }
            steps {
                sh 'npm install'
                sh './node_modules/gulp/bin/gulp.js lint-css'
            }
        }
        stage('lint-js') {
          agent {
              docker {
                image 'node:9.11.1'
                args  '-u root'
              }
          }
            steps {
                sh 'npm install'
                sh './node_modules/gulp/bin/gulp.js lint-js'
            }
        }
        stage('Deploy-Staging') {
          agent {
              docker {
                image 'node:9.11.1'
                args  '-u root'
              }
          }
            steps {
                sh 'echo "Hello"'
                // sh 'apt-get update -qq && apt-get install -y -qq sshpass'
                // sh "sshpass -p$USER_PASS ssh -o StrictHostKeyChecking=no $USER@$SERVER_IP \"cd $STAGING_DIR && git pull -f\""
            }
        }
        stage('Functionize-CLI') {
          agent {
              docker {
                image 'node:9.11.1'
                args  '-u root'
              }
          }
            steps {
              sh 'export PROJECT_DEPLOYMENT_ID=004ba9e8536fc9a9ad6349a12121269b'
              sh 'echo from Command $PROJECT_DEPLOYMENT_ID'
              // sh 'rm -rf functionizecli'
              // sh 'git clone https://functionize@bitbucket.org/functionize/functionizecli.git'
              // sh 'cd functionizecli && npm install'
              // sh 'cd functionizecli && npm install -g'
              // sh 'cd functionizecli && wget -O - https://bitbucket.org/functionize/functionizecli/raw/master/ThirdParty_run.sh | bash'
            }
        }

        // input 'Continue to deploy stage?'

        stage('Deploy-Production') {
          input 'Deploy to Production?'
          agent {
              docker {
                image 'node:9.11.1'
                args  '-u root'
              }
          }
            steps {
                sh 'echo "Hello"'
                // sh 'apt-get update -qq && apt-get install -y -qq sshpass'
                // sh "sshpass -p$USER_PASS ssh -o StrictHostKeyChecking=no $USER@$SERVER_IP \"cd $PRODUCTION_DIR && git pull -f\""
            }
        }
    }
  }
