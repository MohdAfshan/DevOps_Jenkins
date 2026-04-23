pipeline {
    agent any

    stages {

        stage('Clone from GitHub') {
            steps {
                echo 'Cloning repository...'
                git branch: 'main', url: 'https://github.com/your-username/your-repo.git'
            }
        }

        stage('Build - Install Dependencies') {
            steps {
                echo 'Installing Python dependencies...'
                sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests with pytest...'
                sh '''
                    . venv/bin/activate
                    pytest test_app.py -v
                '''
            }
        }

        stage('Deploy - Execute Script') {
            steps {
                echo 'Deploying / Running the application...'
                sh '''
                    . venv/bin/activate
                    python3 app.py
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
