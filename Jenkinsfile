pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/svitlanaBurba/HT2_Dropbox_API', branch: 'main')
      }
    }

    stage('Logging') {
      parallel {
        stage('Logging') {
          steps {
            sh 'ls -la'
          }
        }

        stage('Running Tests') {
          agent {
            node {
              label 'Run tests'
            }

          }
          environment {
            APPKEY = '7ci75ruo3bydihz'
            APPSECRET = '38h9zwlv5foanjt'
            APPTOKEN = 'uhbmPgx95y8AAAAAAAAAAQdakdXlAa-97j2364VC5ZqAyQAw5jdFkFtd6QYM4BIf'
          }
          steps {
            sh '''npm i &&
npm run test_with_creds'''
          }
        }

      }
    }

  }
}