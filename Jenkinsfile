pipeline {
    agent any

    stages {
        stage('Clonar Repo') {
            steps {
                git url: 'https://github.com/FabioJordao97/puc-jenks.git', branch: 'main'
            }
        }
        stage('Instalar Newman') {
            steps {
                // no Windows, use 'bat' ao invés de 'sh'
                bat 'npm install -g newman'
            }
        }
        stage('Rodar testes Postman') {
            steps {
                bat 'newman run collection.json'
            }
        }
    }
}
