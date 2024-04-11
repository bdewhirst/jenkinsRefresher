pipeline {
    agent any
    stages {

        stage('Checkout Codebase-- note: calling this file 'Jenkinsfile' is not arbitrary, and is specified over in Jenkins') {
            steps {
            checkout scm: [$class: 'GitSCM',
            userRemoteConfigs: [[credentialsId: 'jenkins-side-ssh-key-we-set-up',url: 'git@github.com:mnorm88/multithreading-example-1.git']]]

            }
        }
        stage('Build-- recall that 'sh' runs the following command as if it were at the shell') {
            steps {
                sh 'gcc mt-example-0.c -lpthread'

            }
        }
        stage('Test-- in the sense it tries to run the c program which was (hopefully) just built') {
            steps {
                sh './a.out'
            }
        }
        stage('Deploy-- in practice, it'd push the result to production') {
            steps {
                sh 'echo Done!'
            }
        }
    }
}
