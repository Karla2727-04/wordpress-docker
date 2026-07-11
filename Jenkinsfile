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
                bat 'dir'
            }
        }

        stage('Verificar Docker') {
            steps {
                bat 'docker --version'
            }
        }

        stage('Finalizado') {
            steps {
                echo 'Pipeline ejecutado correctamente'
            }
        }
    }
}