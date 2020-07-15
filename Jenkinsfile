pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 sh 'echo "Hello World1"'
                 sh '''
                     echo "Multiline shell steps works too"
                     ls -lah
                 '''
             }
         }
         stage('Lint HTML') {
              steps {
                   sh 'echo "Linting with Tidy"'
                   sh 'tidy -q -e *.html'
              }
         }
         stage('Upload to AWS') {
              steps {
                  withAWS(region:'eu-west-1',credentials:'aws-static') {
                  sh 'echo "Uploading content with AWS creds"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'INSERT BUCKET NAME HERE')
                  }
              }
         }
     }
}
