pipeline {
    agent {
        docker {
            image 'node:22'
        }
    }
    environment {
        NETLIFY_SITE_ID = '248c92b0-e710-4a73-8fc7-1378a7390781'
        NETLIFY_AUTH_TOKEN = credentials('myreactapp-netlify')
    }
    stages {
        stage('Install') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test -- --watchAll=false'
            }
        }
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        stage('Deploy') {
            steps {
                sh 'npx netlify deploy --dir=build --prod --site=$NETLIFY_SITE_ID --auth=$NETLIFY_AUTH_TOKEN'
            }
        }
    }
}