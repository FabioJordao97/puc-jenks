pipeline {
    agent any

    stages {
        stage('Clonar Repositório') {
            steps {
                git branch: 'main', url: 'https://github.com/FabioJordao97/puc-jenks.git'
            }
        }

        stage('Instalar Newman') {
            steps {
                bat 'npm install newman'
            }
        }

        stage('Listar Arquivos') {
            steps {
                bat 'dir /s /b'
            }
        }

        stage('Executar Testes Postman') {
            steps {
                // Ajuste o caminho e nome do arquivo conforme seu repositório
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
