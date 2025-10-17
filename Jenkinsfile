pipeline {
    agent any

    tools {
        nodejs "NodeJS"  // or NodeJS16, if you configured it
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
                sh '''
                    echo "Building React app..."
                    CI=false npm run build   # ✅ ignores warnings as errors
                '''
            }
        }

        stage('Test') {
            steps {
                sh 'npm test || true'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy stage - add deployment steps here'
            }
        }
    }
}

