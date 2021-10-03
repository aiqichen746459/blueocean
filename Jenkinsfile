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
      }
    }

  }
  environment {
    build = '-p 3000:3000'
    deploy = '-p 3000:3000'
  }
}