pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Clona seu repo
                git 'https://github.com/FabioJordao97/puc-jenks.git'
            }
        }

        stage('Install Newman') {
            steps {
                bat 'npm install newman'
            }
        }

        stage('List Workspace Files') {
            steps {
                // Para garantir que o arquivo está no workspace (debug)
                bat 'dir /s /b'
            }
        }

        stage('Run Postman Collection') {
            steps {
                // Rode o Newman com o caminho correto
                bat 'node_modules\\.bin\\newman run postman-collections\\aula_2_puc.postman_collection.json'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finalizado.'
        }
    }
}
