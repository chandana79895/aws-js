pipeline {
  agent any
  environment {
    PULUMI_ACCESS_TOKEN = credentials('jenkins-pulumi')
  }
  stages {
    stage('verify tools') {
      steps {
        sh '''
          pulumi version
        '''
      }
    }
    stage('Pulumi up') {
      steps {
        sh '''
           pulumi stack select "${PULUMI_STACK}"
           pulumi config set aws:region us-west-2
           pulumi up --yes
        '''
      }
    }
  }
}
