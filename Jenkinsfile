@Library("Shared") _
pipeline {
    agent { label "kaako" }

    stages {
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code") {
            steps {
                script{
                clone("https://github.com/Ayush05158/shubham-django-notes-app.git", "main")
                echo "Code cloned successfully"
            }
          }
        }

        stage("Build") {
            steps {
                script{
                    docker_build("notes-app","latest","ayushdocker05158")
                }
            }
        }

        stage("Push to Docker hub") {
            steps {
                script{
                    docker_push("notes-app","latest","ayushdocker05158")
                }
            }
        }

        stage("Deploy") {
            steps {
                echo "This is deploying the code"
                sh "docker compose up -d"
            }
        }
    }
}
