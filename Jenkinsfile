pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/JAKELINESCV/jenkins-release-demo.git'
            }
        }

        stage('Build') {
            steps {
                echo "Compilando aplicación..."
            }
        }

        stage('Test') {
            steps {
                echo "Ejecutando pruebas..."
            }
        }

        stage('Package Release') {
            steps {
                echo "Generando artefacto release..."
                sh 'zip -r release.zip ./src'
            }
        }

        stage('Publish Artifact') {
            steps {
                echo "Publicando artefacto..."
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: 'release.zip', fingerprint: true
            echo "Release generado exitosamente."
        }
        failure {
            echo "Falló el release."
        }
    }
}
