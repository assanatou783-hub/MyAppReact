
pipeline {
    agent any

    options {
        timestamps()
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Recuperation du projet'
                checkout scm
            }
        }

        stage('Verification Docker') {
            steps {
                bat 'docker version'
                bat 'docker compose version'
            }
        }

        stage('Build Docker Compose') {
            steps {
                bat 'docker compose build'
            }
        }

        stage('Lancement des conteneurs') {
            steps {
                bat 'docker compose up -d'
            }
        }

        stage('Verification des conteneurs') {
            steps {
                bat 'docker compose ps'
            }
        }

        stage('Verification de l application') {
            steps {
                bat 'curl -f http://localhost:3000'
            }
        }
    }

    post {
        always {
            echo 'Fin du pipeline Jenkins'
        }
        success {
            echo 'Pipeline execute avec succes'
        }
        failure {
            echo 'Echec du pipeline : verifier les logs'
        }
    }
}
