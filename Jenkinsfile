pipeline {
  agent any

  environment {
    // Ajusta si tu PATH difiere
    PATH = "/Users/oscar/.nvm/versions/node/v22.19.0/bin:/usr/bin:/bin:/usr/sbin:/sbin"
  }

  stages {

    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Validate Environment') {
      steps {
        sh 'which node'
        sh 'node -v'
        sh 'npm -v'
      }
    }

    stage('Install Dependencies') {
      steps {
        sh 'npm install'
      }
    }

    stage('Run API Tests (Newman)') {
      steps {
        sh 'npm run test:api'
      }
    }
  }

  post {
    always {
      // Publica resultados JUnit
      junit 'reports/*.xml'

      // Publica reporte HTML
      publishHTML(target: [
        reportDir: 'reports',
        reportFiles: 'index.html',
        reportName: 'Newman API Test Report',
        keepAll: true,
        alwaysLinkToLastBuild: true,
        allowMissing: false
      ])
    }

    success {
      echo '✅ Pruebas API exitosas'
    }

    failure {
      echo '❌ Fallaron pruebas API'
    }
  }
}
