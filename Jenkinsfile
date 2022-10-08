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
            sh 'npm i & npm run test'
          }
        }

      }
    }

  }
}