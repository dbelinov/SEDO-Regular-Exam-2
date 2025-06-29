pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Restore') {
      steps {
        echo 'Restoring dependencies...'
        sh 'dotnet restore'
      }
    }

    stage('Build') {
      steps {
        echo 'Building the application...'
        sh 'dotnet build --configuration Release --no-restore'
      }
    }

    stage('Test') {
      steps {
        echo 'Running tests...'
        sh 'dotnet test --configuration Release --no-build --logger "trx;LogFileName=test_results.trx"'
      }
    }
  }
}