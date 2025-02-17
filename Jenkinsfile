pipeline {
    agent any
    stages {
        stage('Install Vercel') {
            steps {
                sh 'npm install -g vercel'
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Deploy') {
            steps {
                withCredentials([string(credentialsId: 'vercel-token', variable: 'VERCEL_TOKEN')]) {
                    sh "vercel --token $VERCEL_TOKEN --prod --yes"
                }
            }
        }
    }
}
