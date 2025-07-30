pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git credentialsId: 'github-creds',
            url: 'https://github.com/mansoorsheikh1982/nodejs-pg-app.git',
            branch: 'main'
      }
    }

    stage('Install Dependencies') {
      steps {
        sh 'npm install'
      }
    }

    stage('Test DB Connection') {
      steps {
        sh 'node test-db.js'
      }
    }

    stage('Start App') {
      steps {
        sh 'npm start'
      }
    }
  }

  post {
    failure {
      echo '🚨 Build or deployment failed.'
    }
  }
}

