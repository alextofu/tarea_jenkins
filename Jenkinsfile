pipeline {
    agent any
    stages {
        stage('Install Vercel') {
            steps {
                script {
                    // Set a local npm global directory that Jenkins user has permissions to
                    sh 'mkdir -p ~/.npm-global'
                    sh 'npm config set prefix ~/.npm-global'
                    sh 'npm install -g vercel'
                }
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
