pipeline {
    agent any

    environment {
        VENV_DIR = "venv"
    }

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
                    echo "Creating virtual environment..."
                    python3 -m venv $VENV_DIR

                    echo "Activating venv..."
                    . $VENV_DIR/bin/activate

                    echo "Upgrading pip..."
                    pip install --upgrade pip

                    if [ -f requirements.txt ]; then
                        echo "Installing dependencies..."
                        pip install -r requirements.txt
                    else
                        echo "No requirements.txt found"
                    fi
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    echo "Running tests..."
                    . $VENV_DIR/bin/activate

                    if command -v pytest >/dev/null 2>&1; then
                        pytest
                    else
                        echo "pytest not installed, skipping tests"
                    fi
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    echo "Deploying application..."
                    . $VENV_DIR/bin/activate

                    pkill -f app.py || true
                    nohup python3 app.py > app.log 2>&1 &
                '''
            }
        }
    }

    post {
        success {
            echo "✅ Pipeline completed successfully"
        }
        failure {
            echo "❌ Pipeline failed"
        }
    }
}
