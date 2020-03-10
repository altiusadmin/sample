pipeline {
    agent none

    options {
      buildDiscarder(logRotator(numToKeepStr: '5'))
    }    

    stages {
        stage('Checkout'){
            agent {
                docker {
                    image 'ruby:2.7'
                    args '-v /var/run/docker.sock:/var/run/docker.sock -v /usr/bin/docker:/usr/bin/docker'
                }
            }
            steps {
                checkout scm
            }
        }

        stage('Code Backup'){
            agent any
            steps {
                sh 'tar cvzf sample-$BUILD_TIMESTAMP.tar.gz $WORKSPACE/'
                sh 'mv sample-$BUILD_TIMESTAMP.tar.gz /home/ubuntu/code_backup/sample/'
            }
        }
    }    
}