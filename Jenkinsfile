pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/akranthi113/practicedevops.git'
            }
        }

        stage('Build') {
            steps {
                sh 'echo "Building the app..."'
            }
        }

        stage('Test') {
            steps {
                sh 'pytest || echo "No tests yet"'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker build -t myapp .'
                sh 'docker run -d -p 5000:5000 myapp'
            }
        }
    }
}
