@Library("Shared") _
pipeline{
    
    agent { label "vinod" }
    
    environment {
        MAVEN_HOME = "/mnt/c/Program Files/apache-maven-3.9.11"
        PATH = "${MAVEN_HOME}/bin:${env.PATH}"
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
                    clone("https://github.com/shivamjaswal/java-basic-app.git","main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build("basic-app", "latest", "shivamjaswal")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("basic-app", "latest", "shivamjaswal")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose up -d"
            }
        }
        
    }
    
}
