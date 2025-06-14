pipeline {
    agent any

    stages {
        stage('Clean Workspace') {
            steps {
                cleanWs()
            }
        }
        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/FabioJordao97/puc-jenks.git'
            }
        }
        stage('Check Files') {
            steps {
                echo "Listando arquivos pra garantir que a collection está aqui..."
                bat 'dir /s /b'
            }
        }
        stage('Install Newman') {
            steps {
                bat 'npm install newman'
            }
        }
        stage('Run Newman Tests') {
            steps {
                echo "Executando Newman na collection..."
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
