pipeline {
  agent {
    node {
      label 'heros'
    }

  }
  stages {
    stage('build') {
      steps {
        git 'https://github.com/johnpapa/heroes-angular'
        bat 'git clone https://github.com/johnpapa/heroes-angular.git'
      }
    }

  }
  environment {
    build = '-p 3000:3000'
    deploy = '-p 3000:3000'
  }
}