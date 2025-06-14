pipeline {
    agent any

    stages {
        stage('Limpar workspace') {
            steps {
                echo 'Limpando o workspace atual...'
                deleteDir() // Limpa arquivos do workspace
            }
        }

        stage('Clonar repositório') {
            steps {
                echo 'Clonando repositório do GitHub...'
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/main']], // Use '*/master' se o branch for master
                    userRemoteConfigs: [[url: 'https://github.com/FabioJordao97/puc-jenks.git']]
                ])
            }
        }

        stage('Instalar dependências') {
            steps {
                echo 'Instalando pacotes com npm...'
                bat 'npm install'
            }
        }

        stage('Executar testes Postman') {
            steps {
                echo 'Executando coleção Postman com Newman...'
                bat 'node_modules\\.bin\\newman run aula_2_puc.postman_collection.json'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finalizado.'
        }
        failure {
            echo 'Pipeline falhou! Verifique o console output.'
        }
    }
}
