@Library("Shared") _
pipeline {
    
    agent { label 'vinod' }
    
    stages {
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Clone") {
            steps {
                script{
                    gitClone("https://github.com/avinavvv/django-notes-app.git", "main")
                }
            }
        }
        stage("Build") {
            steps {
                script{
                    docker_build("notes-app","latest","avinavv")
                }
            }
        }
        stage("Push To DockerHub") {
            steps {
                script{
                    docker_push("notes-app","latest","avinavv")
                }
            }
        }
        stage("Deploy") {
            steps {
                echo "This is deploying the code"
                sh 'docker compose down --remove-orphans || true'
                sh 'docker compose up -d --no-build --remove-orphans'
            }
        }
    }
}
