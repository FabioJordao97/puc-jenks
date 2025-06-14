pipeline {
    agent any

    environment {
        // Define variáveis se quiser
    }

    stages {
        stage('Limpar workspace') {
            steps {
                echo 'Limpando o workspace atual...'
                deleteDir()  // Limpa tudo no workspace antes do build
            }
        }

        stage('Clonar repositório') {
            steps {
                echo 'Clonando repositório...'
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/main']],  // ou '*/master' se for o nome do branch correto
                    userRemoteConfigs: [[url: 'https://github.com/FabioJordao97/puc-jenks.git']]
                ])
            }
        }

        stage('Instalar dependências') {
            steps {
                echo 'Instalando dependências...'
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
            echo 'Pipeline falhou! Verifique os logs para detalhes.'
        }
    }
}
