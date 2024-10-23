pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Сборка Docker-образа
                    def app = docker.build("my-devops-app")
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Тестирование Docker-образа
                    app.inside {
                        sh 'python -m unittest discover'
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Запуск Docker-контейнера
                    docker.image("my-devops-app").run("-d -p 8080:80")
                }
            }
        }
    }
}
