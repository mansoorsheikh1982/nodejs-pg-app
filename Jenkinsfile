pipeline {
    agent any

    environment {
        DB_USER = 'postgres'
        DB_PASS = 'postgres'
        DB_NAME = 'testdb'
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/YOUR-USERNAME/nodejs-pg-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test DB Connection') {
            steps {
                sh 'psql -U $DB_USER -d $DB_NAME -c "SELECT NOW();"'
            }
        }

        stage('Start App') {
            steps {
                sh 'nohup npm start &'
            }
        }
    }

    post {
        success {
            echo '✅ Node.js app deployed successfully.'
        }
        failure {
            echo '❌ Build or deployment failed.'
        }
    }
}
