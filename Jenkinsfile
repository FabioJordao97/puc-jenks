pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Clona o seu repo
                git url: 'https://github.com/FabioJordao97/puc-jenks.git', branch: 'main'
            }
        }

        stage('Instalar dependências') {
            steps {
                // Instala npm para que o newman funcione
                bat 'npm install'
            }
        }

        stage('Executar testes Postman') {
            steps {
                // Roda o newman na collection que está no root
                bat 'node_modules\\.bin\\newman run aula_2_puc.postman_collection.json'
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
            echo 'Pipeline falhou. Verifique o console output.'
        }
    }
}
