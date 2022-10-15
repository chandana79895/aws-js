pipeline {
    agent any
   environment {
  stages {
    stage('verify tools') {
      steps {
        sh '''
          node -v
          npm -v
          pulumi version
        '''
      }
    }
    stage('up') {
      environment {
        PULUMI_STACK = getPulumiStack()
      }
      steps {
        sh '''
           npm install
           pulumi stack select ${PULUMI_STACK}
           pulumi up --yes
        '''
      }
    }
  }
   }
}
