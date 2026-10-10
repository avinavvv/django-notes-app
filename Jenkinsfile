@Library("Shared") _
pipeline {
    agent { label 'vinod' }

    stages {
        stage("Clone") {
            steps {
                script {
                    clone("https://github.com/avinavvv/django-notes-app.git", "main")
                }
            }
        }

        stage("Build") {
            steps {
                script {
                    docker_build("notes-app", "latest", "avinavv")
                }
            }
        }

        stage("Push To DockerHub") {
            steps {
                script {
                    docker_push("notes-app", "latest", "avinavv")
                }
            }
        }

        stage("Deploy") {
            steps {
                script {
                    docker_compose()
                }
            }
        }
    }
}
