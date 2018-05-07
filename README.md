<h1 align="center">
  <br>
   <img src="https://app.functionize.com/views/images/logo/logo-small.png"/>
  <br>
</h1>
<p align="center">
<img src="https://codebuild.us-east-1.amazonaws.com/badges?uuid=eyJlbmNyeXB0ZWREYXRhIjoiRDZtT2hjbEJYcGg3TllTZ0xuZVlCeThrYzEwNDIxOHZjQ0dQY09wbkdGV2NabGJXNlpxNUl1dDI5aThsMmpVYjRDNE04dTdaWXNPTXlVKzl6aHJKUWlvPSIsIml2UGFyYW1ldGVyU3BlYyI6InZtQzB2TXdWZXZWMjQwUUQiLCJtYXRlcmlhbFNldFNlcmlhbCI6MX0%3D&branch=master"></a>
<p align="center">
  This repository contains Example Of Intregrating <strong>Functionize Smart Testing Tool </strong>with <strong>Jenkins CI</strong>
</p>

### Including Functionize TestsSuite in CodeBuild CI.

Requires Active Functionize.com Account.

Include This Snippet In any of the Stage/Phase, Where you want to run test-cases.
```bash
pipeline {
    agent none
    stages {
      stage('Functionize-CLI') {
        agent {
            docker {
              image 'node:9.11.1'
              args  '-u root'
            }
        }
          steps {
            sh 'rm -rf functionizecli'
            sh 'git clone https://functionize@bitbucket.org/functionize/functionizecli.git'
            sh 'cd functionizecli && npm install'
            sh 'cd functionizecli && npm install -g'
            sh 'wget -O - https://bitbucket.org/functionize/functionizecli/raw/master/ThirdParty_run.sh | bash'
          }
      }
```

## Parameters

You Need to Pass Some Parameters To make it work. Everything Can be get from app.functionize.com acccount.

| `Parameter`               | `Value`               |
|-------------------------|---------------------------|
| DEPLOYMENT_TIME | 3600 in Sec
| YOUR_SECRET_KEY | Client ID
| YOUR_API_KEY |  Client Secret
| PROJECT_DEPLOYMENT_ID | Orechestration_ID
