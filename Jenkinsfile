pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Clonar o repositório
                checkout scm
            }
        }

        stage('Build and Test') {
            steps {
                // Executar testes com Maven
                sh 'mvn clean verify'
            }
        }

        stage('Generate Coverage Report') {
            steps {
                // Executar o relatório de cobertura com Maven
                sh 'mvn jacoco:report'
            }
        }
    }

    post {
        always {
            // Publicar relatório de cobertura
            publishHTML([allowMissing: false, alwaysLinkToLastBuild: true, keepAll: true, reportDir: 'target/site/jacoco', reportFiles: 'index.html', reportName: 'Coverage Report'])
        }
    }
}
