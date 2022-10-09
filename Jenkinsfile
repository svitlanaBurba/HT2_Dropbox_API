pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git(url: 'https://github.com/svitlanaBurba/HT2_Dropbox_API', branch: 'main')
      }
    }

    stage('Bind Credentials') {
      steps {
        withCredentials(bindings: [usernamePassword(credentialsId: 'Dropbox', usernameVariable: 'APPKEY', passwordVariable: 'APPSECRET')])
      }
    }

    stage('Running Tests') {
      agent any
      environment {
        APPTOKEN = 'uhbmPgx95y8AAAAAAAAAAQdakdXlAa-97j2364VC5ZqAyQAw5jdFkFtd6QYM4BIf'
      }
      steps {
        sh '''npm i &&
npm run test_with_creds'''
      }
    }

  }
}