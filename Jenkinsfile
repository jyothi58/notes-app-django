@Library("Shared") _
pipeline{
    
    agent { label "agent-1"}
    
    stages{
        stage("Code"){
            steps{
               script{
                clone("https://github.com/jyothi58/notes-app-django.git","main")
               }
            }
        }
        stage("Build"){
            steps{
                script{
                docker_build("notes-app","latest","jyothi58")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app","latest","jyothi58")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
