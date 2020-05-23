pipeline {
    agent any
    stages {
       stage('Lint HTML') {
              steps {
                  sh 'echo "starting...."'
                  sh 'tidy -q -e *.html'
                  sh 'echo "ending....."'
              }
         }
       stage('Upload to AWS') {
             steps {
                 withAWS(region:'us-east-1',credentials:'aws-user') {
                 sh 'echo "Uploading content with AWS creds"'
                     s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'jenkins-udacity-project3')
                 }
             }
        }
    }
}
