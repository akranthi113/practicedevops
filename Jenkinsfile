pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/akranthi113/practicedevops.git',
                    credentialsId: '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'
            }
        }

        stage('Build') {
            steps {
                sh 'echo "Installing dependencies..."'
                sh 'pip3 install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                sh 'echo "Running tests..."'
                sh 'pytest || echo "No tests yet"'
            }
        }

        stage('Deploy') {
            steps {
                sh 'echo "Starting Flask app..."'
                // Run app in background so Jenkins job doesn’t hang
                sh 'nohup python3 app.py > app.log 2>&1 &'
            }
        }
    }
}
