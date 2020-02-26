pipeline {
    agent {
        docker {
            image 'ruby:2.7'
            args '-v /var/run/docker.sock:/var/run/docker.sock -v /usr/bin/docker:/usr/bin/docker'
        }
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
                sh 'rake db:create db:migrate'
            }
        }

    }    
}