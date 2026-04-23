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
                echo 'Installing dependencies...'
                bat '''
                "C:\\Users\\Mohammed Afshan\\AppData\\Local\\Programs\\Python\\Python314\\python.exe" -m pip install --upgrade pip
                "C:\\Users\\Mohammed Afshan\\AppData\\Local\\Programs\\Python\\Python314\\python.exe" -m pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                bat '''
                "C:\\Users\\Mohammed Afshan\\AppData\\Local\\Programs\\Python\\Python314\\python.exe" -m unittest discover
                '''
            }
        }

        stage('Deploy - Execute Script') {
            steps {
                echo 'Running application...'
                bat '''
                "C:\\Users\\Mohammed Afshan\\AppData\\Local\\Programs\\Python\\Python314\\python.exe" app.py
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline finished successfully!'
        }
        failure {
            echo '❌ Pipeline failed. Check logs.'
        }
    }
}
