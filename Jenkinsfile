pipeline {
    agent any

    environment {
        DOCKER_IMAGE = ''
    }

    stages {
        stage('Build') {
            steps {
                script {
                    // Сборка Docker-образа и сохранение ссылки на образ в переменную DOCKER_IMAGE
                    DOCKER_IMAGE = docker.build("my-devops-app")
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Тстирование Docker-образа
                    DOCKER_IMAGE.inside {
                        sh 'python -m unittest discover'
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Запуск Docker-контейнера
                    DOCKER_IMAGE.run("-d -p 8081:80")
                }
            }
        }
    }
}

