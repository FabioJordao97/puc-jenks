pipeline {
    agent any

    stages {
        stage('Clonar Repositório') {
            steps {
                git url: 'https://github.com/FabioJordao97/puc-jenks.git', branch: 'main'
            }
        }
        stage('Listar arquivos detalhado') {
            steps {
                bat 'dir /s /b'
            }
        }
        stage('Instalar Newman') {
            steps {
                bat 'npm install newman'
            }
        }
        stage('Executar Testes Postman') {
            steps {
                // Ajuste o nome do arquivo conforme o resultado da listagem, aqui é um exemplo genérico
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
