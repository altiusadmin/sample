pipeline {
    agent {
        docker {
            image 'python:2.7'
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

        stage('Code Backup'){
            steps {
                sh 'echo hello'
            }
        }
    }    
}