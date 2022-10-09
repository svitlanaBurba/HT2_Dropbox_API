pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git(url: 'https://github.com/svitlanaBurba/HT2_Dropbox_API', branch: 'main')
      }
    }

    stage('Running Tests') {
      agent any
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