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
                sh 'echo "Building the app..."'
                // Example: if Python Flask
                // sh 'pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                sh 'echo "Running tests..."'
                // Example: pytest
                // sh 'pytest || echo "No tests yet"'
            }
        }

        stage('Deploy') {
            steps {
                sh 'echo "Deploying app..."'
                // Example: Docker deployment
                // sh 'docker build -t myapp .'
                // sh 'docker run -d -p 5000:5000 myapp'
            }
        }
    }
}
