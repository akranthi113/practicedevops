pipeline {
  agent any

 stage('Checkout') {
    steps {
        git branch: 'main', url: 'https://github.com/akranthi113/practicedevops.git'
    }
}
    }

    stage('Build Image') {
      steps {
        sh 'docker build -t jenkins-demo .'
      }
    }

    stage('Test') {
      steps {
        sh 'npm test'
      }
    }

    stage('Deploy') {
      steps {
        sh '''
          docker stop demo || true
          docker rm demo || true
          docker run -d -p 3000:3000 --name demo jenkins-demo
        '''
      }
    }
  }
}
