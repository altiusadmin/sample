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
                    DATE_TAG = java.time.LocalDate.now()
                    DATETIME_TAG = java.time.LocalDateTime.now()
                }
                sh "echo ${JOB_BASE_NAME}"
                sh "tar cvzf ${JOB_BASE_NAME}-${DATE_TAG}.tar.gz $WORKSPACE/"
                sh "mv $WORKSPACE/${JOB_BASE_NAME}-${DATE_TAG}.tar.gz /root/code_backup/sample"
            }
        }
    }    
}