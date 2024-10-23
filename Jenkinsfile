pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Сборка Docker-образа и сохранение ссылки на образ в переменную app
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
                    // Деплой Docker-контейнера
                    app.run("-d -p 8080:80")
                }
            }
        }
    }
}

