pipeline {
     agent any
      stage('Lint HTML') {
              steps {
                  sh 'tidy -q -e *.html'
              }
     stages {   
         stage('Upload to AWS') {
              steps {
                  withAWS(region:'us-east-2',credentials:'aws-static') {
                  sh 'echo "Uploading content with AWS credis"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'jenkinsbukt')
                  }
              }
         }   
     }
}
