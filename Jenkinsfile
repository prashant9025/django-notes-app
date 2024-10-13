@Library("Shared") _
pipeline{
    
    agent {label "prashant"}
    
    stages{
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
            
        }
        stage("code"){
            steps{
                script{
                clone("https://github.com/prashant9025/django-notes-app.git","main")
                }
            }
            
        }
        stage("Build"){
            steps{
                script{
                docker_build("notes-app","latest","prashant9025")
                }
            }
            
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app","latest","prashant9025")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is Dploying the code"
                sh "docker compose up -d"
            }
            
        }
    }
}
