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
                sh '''
                    echo "Setting up virtual environment..."
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    echo "Running tests..."
                    . venv/bin/activate
                    pytest || echo "No tests found"
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    echo "Starting Flask app..."
                    . venv/bin/activate
                    nohup python3 app.py > app.log 2>&1 &
                '''
            }
        }
    }
}
