pipeline {
    agent any

    stages {

        stage('Checkout desde Git') {
            steps {
                echo 'Repositorio descargado correctamente'
            }
        }

        stage('Docker Compose Down') {
            steps {
                sh 'docker compose down --remove-orphans || true'
                sh 'docker rm -f wordpress-db wordpress-app || true'
            }
        }

        stage('Docker Compose Up') {
            steps {
                sh 'docker compose up -d'
            }
        }

        stage('Verificar despliegue') {
            steps {
                sh 'docker ps'
            }
        }
    }
}