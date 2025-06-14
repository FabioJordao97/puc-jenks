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
                    branches: [[name: '*/main']], // ou '*/master' se for o seu caso
                    userRemoteConfigs: [[url: 'https://github.com/FabioJordao97/puc-jenks.git']]
                ])
            }
        }

        stage('Executar testes Postman') {
            steps {
                echo 'Executando testes com Newman...'
                bat 'newman run aula_2_puc.postman_collection.json'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finalizado.'
        }
        failure {
            echo 'Pipeline falhou. Veja o console output.'
        }
    }
}
