@Library("shared") _
pipeline{
    
    agent { label "dev"}
    
    stages{
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
               script{
                clone("https://github.com/LondheShubham153/django-notes-app.git","main")
               }
                
            }
        }
        stage("Build"){
            steps{
                script{
                    docker build -t notes-app .
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app","latest","trainwithshubham")
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
