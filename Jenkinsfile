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
          steps {
            sh '''npm i && 
npm i -g newman &&
newman run collection_dropbox_api.json --globals globals.json --global-var "appKey=7ci75ruo3bydihz"  --global-var "appSecret=38h9zwlv5foanjt"  --global-var "refreshToken=uhbmPgx95y8AAAAAAAAAAQdakdXlAa-97j2364VC5ZqAyQAw5jdFkFtd6QYM4BIf"'''
          }
        }

      }
    }

  }
}