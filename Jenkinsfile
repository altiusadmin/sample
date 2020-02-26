pipeline {
    agent any

    options {
      buildDiscarder(logRotator(numToKeepStr: '5'))
    }    

    stages {
        stage('Checkout'){
            steps {
                checkout scm
            }
        }

        stage('Bundle Install'){
            steps {
                sh 'sudo gem install bundler'
                sh 'sudo bundle install'
            }
        }

        stage('Rake DB'){
            steps {
                sh 'sudo rake db:create db:migrate'
            }
        }

    }    
}