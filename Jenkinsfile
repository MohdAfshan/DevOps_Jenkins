pipeline {
    agent any

    stages {

        stage('Clone from GitHub') {
            steps {
                echo 'Cloning repository...'
                git branch: 'main', url: 'https://github.com/MohdAfshan/DevOps_Jenkins'
            }
        }

        stage('Build - Install Dependencies') {
            steps {
                echo 'Installing Python dependencies...'
                bat '''
                    python -m pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                bat '''
                    python -m unittest discover
                '''
            }
        }

        stage('Deploy - Execute Script') {
            steps {
                echo 'Running the application...'
                bat '''
                    python app.py
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline finished successfully!'
        }
        failure {
            echo '❌ Pipeline failed. Check the Console Output for errors.'
        }
    }
}
