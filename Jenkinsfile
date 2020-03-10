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
                script {
                    DATETIME_TAG=$(date '+%Y-%m-%d')
                }
                sh 'tar cvzf sample-${DATETIME_TAG}.tar.gz $WORKSPACE/'
                sh 'mv sample-${DATETIME_TAG}.tar.gz /home/ubuntu/code_backup/sample/'
            }
        }
    }    
}