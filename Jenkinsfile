pipeline {
    agent any

    stages {
        stage('Preparar entorno') {
            steps {
                echo 'Preparando entorno Docker'
            }
        }

        stage('Verificar archivos') {
            steps {
                sh 'ls -la'
            }
        }

        stage('Verificar Docker') {
            steps {
                sh 'docker --version'
            }
        }

        stage('Finalizado') {
            steps {
                echo 'Pipeline ejecutado correctamente'
            }
        }
    }
}