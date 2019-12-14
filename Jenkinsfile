pipeline {
   agent any

   environment {

     SERVICE_NAME = "fin-trading-app-mongodb"
     REPOSITORY_TAG="${YOUR_DOCKERHUB_USERNAME}/${ORGANIZATION_NAME}-${SERVICE_NAME}:${BUILD_ID}"
   }

   stages {
      stage('Preparation') {
         steps {
            cleanWs()
            git credentialsId: 'GitHub', url: "https://github.com/${ORGANIZATION_NAME}/${SERVICE_NAME}"
         }
      }
      stage('Build') {
         steps {
            sh '''echo No build required for Mongodb'''
         }
      }

      stage('Build and Push Image') {
         steps {
           sh 'echo No docker image for Mongodb'
         }
      }

      stage('Deploy to Cluster') {
          steps {
            //sh 'cd /tmp'
            //sh 'wget https://www.openssl.org/source/openssl-1.1.1.tar.gz'
            //sh 'tar xvf openssl-1.1.1.tar.gz'
            //sh 'cd openssl-1.1.1'
            //sh 'sudo ./config -Wl,--enable-new-dtags,-rpath,'$(LIBRPATH)''
            //sh 'sudo make'
            //sh 'sudo make install'
             //sh 'openssl rand -base64 741 > ./key.txt'
             sh 'apt-get install'
             sh 'apt-get install libssl-dev'
             sh 'export FOO=${WORKSPACE}'
             sh 'kubectl create secret generic shared-bootstrap-data --from-file=internal-auth-mongodb-keyfile=./key.txt'  
             sh 'envsubst < ${WORKSPACE}/deploy.yml | kubectl apply -f -'

          }
      }
   }
}
