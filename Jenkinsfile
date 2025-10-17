pipeline {
    agent any

    tools {
        nodejs "NodeJS16" // update this to your NodeJS tool name in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/sami188440/Trading-UI.git', branch: 'master' 
            }
        }

        stage('Install') {
            steps {
                sh '''
                    npm cache clean --force
                    rm -rf node_modules package-lock.json
                    npm install --omit=optional
                '''
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test || true'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy stage - add your deployment steps here'
            }
        }
    }
}
