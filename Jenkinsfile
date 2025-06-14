pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/FabioJordao97/puc-jenks.git', branch: 'main'
            }
        }

        stage('Instalar dependências') {
            steps {
                bat 'npm install'
            }
        }

        stage('Executar testes Postman') {
            steps {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    bat 'node_modules\\.bin\\newman run aula_2_puc.postman_collection.json'
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline finalizado.'
        }
        success {
            echo 'Build executado com sucesso!'
        }
        failure {
            echo 'Pipeline falhou em algum stage.'
        }
    }
}
