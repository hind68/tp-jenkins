pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'javac Main.java'
            }
        }

        stage('Run') {
            steps {
                sh 'java Main > resultat.txt'
            }
        }

        stage('Test') {
            steps {
                sh 'grep -qi "hello" resultat.txt'
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: '*.class, resultat.txt'
        }

        failure {
            echo 'Le pipeline a échoué'
        }
    }
}