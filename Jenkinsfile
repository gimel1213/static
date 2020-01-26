pipeline {
  agent any
  stages {
    stage('Lint HTML') {
      steps {
        sh 'tidy -q -e *.html'
      }
    }

    stage('Upload to AWS') {
      steps {
        withAWS(region: 'us-east-1', credentials: 'awscredentials ') {
          s3Upload(bucket: 'static-web-site-udacity', includePathPattern: '**/*')
        }

      }
    }

  }
}