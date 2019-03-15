pipeline {
  agent any
  stages {
    stage('Install') {
      steps {
        sh 'npm install'
      }
    }
    stage('Build') {
      steps {
        sh 'npm run build'
      }
    }
    stage('Test') {
      steps {
        sh 'npm test'
        emailext(subject: 'Autorizar', body: 'favor de Autorizar', attachLog: true, to: 'Arturo')
      }
    }
    stage('Aprobar') {
      steps {
        input(message: 'aprobar', submitterParameter: 'Sergio')
      }
    }
    stage('Deploy') {
      steps {
        sh 'echo "Listo"'
      }
    }
  }
  environment {
    TARGET_SERVER_USER = 'ec2-user'
    TARGET_SERVER_HOST = '52.15.213.43'
  }
}