pipeline {
    agent none

    options {
      buildDiscarder(logRotator(numToKeepStr: '5'))
    }    

    stages {
        agent {
                docker {
                    image 'ruby:2.7'
                    args '-v /var/run/docker.sock:/var/run/docker.sock -v /usr/bin/docker:/usr/bin/docker'
                }
            }
        stage('Checkout'){
            steps {
                checkout scm
            }
        }

        stage('Code Backup'){
            agent any
            steps {
                script {
                    DATE_TAG = java.time.LocalDate.now()
                    DATETIME_TAG = java.time.LocalDateTime.now()
                }
                sh 'tar cvzf sample-${DATETIME_TAG}.tar.gz $WORKSPACE/'
            }
        }
    }    
}