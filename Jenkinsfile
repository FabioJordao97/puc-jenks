pipeline {
    agent any

    stages {
        stage('Limpar workspace') {
            steps {
                cleanWs()
            }
        }
        stage('Clonar Repositório') {
            steps {
                git branch: 'main', url: 'https://github.com/FabioJordao97/puc-jenks.git'
            }
        }
        stage('Listar arquivos no workspace') {
            steps {
                bat 'dir /b /s'
            }
        }
        stage('Instalar Newman') {
            steps {
                bat 'npm install newman'
            }
        }
        stage('Executar Testes Postman') {
            steps {
                bat 'node_modules\\.bin\\newman run aula_2_puc.postman_collection.json'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finalizado.'
        }
    }
}
