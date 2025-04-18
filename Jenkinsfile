pipeline {
    agent any

    environment {
        // Set the location where the app will run
        APP_DIR = 'nodejs-app'
    }

    stages {
        stage('Clone Repository') {
            steps {
                // Replace with your actual GitHub repo
                git url: 'https://github.com/your-username/your-nodejs-repo.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Navigate into app directory if needed
                    dir("${APP_DIR}") {
                        sh 'npm install'
                    }
                }
            }
        }

        stage('Deploy Application') {
            steps {
                script {
                    dir("${APP_DIR}") {
                        // Start the application in the background
                        // Use nohup or pm2 if you want it to keep running after pipeline ends
                        sh 'nohup npm start &'
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
