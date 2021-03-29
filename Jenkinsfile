pipeline {
    agent any
    environment {
        MYSQL_ROOT_PASSWORD = "password"
        DOCKER_PASSWORD = credentials("DOCKER_PASSWORD")
    }

    stages {

        stage("Install Dependencies") {
            steps{
                sh "echo $MYSQL_ROOT_PASSWORD"
                sh "bash install-dependencies.sh"
            }
        }

        stage("Build") {
            steps {
                sh "docker-compose build --parallel"
            }
        }

        stage("Push") {
            steps {
                sh "docker-compose push"
            }
        }

        stage("Deploy") {
            steps {
                sh "docker-compose up -d"
            }
        }
    }
}