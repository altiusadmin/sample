pipeline {
    agent {
        any
    }

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
                sh 'gem install bundler'
                sh 'bundle install'
            }
        }

        stage('Rake DB'){
            steps {
                sh 'yarn install --check-files'
                sh 'rake db:create db:migrate'
            }
        }

    }    
}