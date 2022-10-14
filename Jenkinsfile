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
           pulumi config set aws:region us-east-1
           aws s3 ls
           aws configure
           Access Key ID: AKIAR6ZLIUHQY6M7K7XA
           AWS Secret Access Key: 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
           Default region name: us-east-1
           pulumi up --yes
        '''
      }
    }
  }
}
