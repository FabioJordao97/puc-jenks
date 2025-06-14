pipeline {
    agent any

    stages {
        stage('Limpar workspace') {
            steps {
                deleteDir()
                echo 'Workspace limpo.'
            }
        }

        stage('Clonar repositório') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/main']], // ajuste se for master
                    userRemoteConfigs: [[url: 'https://github.com/FabioJordao97/puc-jenks.git']]
                ])
            }
        }

        stage('Instalar Newman') {
            steps {
                echo 'Instalando Newman localmente na workspace...'
                bat 'npm install newman'
            }
        }

        stage('Executar testes Postman') {
            steps {
                echo 'Executando testes com Newman...'
                bat 'node_modules\\.bin\\newman run aula_2_puc.postman_collection.json'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finalizado.'
        }
        failure {
            echo 'Pipeline falhou. Verifique o console output.'
        }
    }
}
