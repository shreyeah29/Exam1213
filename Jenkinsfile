pipeline {
    agent any
    stages {
        stage('compute') {
            steps {
                sh 'javac Factorial.java TestFactorial.java'
            }
        }
        stage('Test') {
            steps {
                sh 'java TestFactorial'
            }
        }
        stage('Run') {
            steps {

                sh 'java Factorial'
            }
        }
        stage('Package JAR') {
            steps {
                sh 'jar cfm Factorial.jar manifest.txt Factorial.class'
            }
        }
        stage('Archive JAR') {
            steps {
                archiveArtifacts artifacts: 'Factorial.jar'
            }
        }
    }
    post {
        success {
            echo 'Build, test, run, and JAR action successful — artifact ready.'
        }
        failure {
            echo 'Build failed.'
        }
    }
}
