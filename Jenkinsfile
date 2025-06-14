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
                    branches: [[name: '*/main']], // use 'master' se o branch for master
                    userRemoteConfigs: [[url: 'https://github.com/FabioJordao97/puc-jenks.git']]
                ])
            }
        }

        stage('Instalar Newman') {
            steps {
                bat 'npm install newman'
            }
        }

        stage('Listar arquivos') {
            steps {
                bat 'dir'
                bat 'dir postman'
            }
        }

        stage('Executar testes Postman') {
            steps {
                bat 'node_modules\\.bin\\newman run postman\\aula_2_puc.postman_collection.json'
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
