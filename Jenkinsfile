@Library("Shared") _
pipeline{
    agent{
        label "vinod"
    }
    
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
                    clone("https://github.com/Nikhil-Mhatre/django-notes-app","main" )
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app", "latest", "dockerHubCred")
                    
                }
            }
        }
        stage("Push To DockerHub"){
            steps{
                script{
                    docker_push("notes-app","latest","dockerHubCred")
                }
            }
        }
        stage("Deploy"){
            steps{
               script{
                   docker_deploy()
               }
            }
        }
   }
}
