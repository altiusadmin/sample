pipeline {
    agent {
        docker {
            image 'node:12.13.0'
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

        stage('Test'){
            steps {
                echo 'coming soon...'
                sh 'node -v'
            }
        }

    }    
}