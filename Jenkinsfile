pipeline {
    agent any
    
    stages {    
        
        stage('build') {
            steps {
                script{
                    dockerImage = docker.build("salarabbas24/mlops_classtask:latest")
                }
            }
        }
        
        stage('push') {
            steps {
                script {
                    withDockerRegistry([credentialsId: "dockerhub", url: "https://registry.hub.docker.com"]) {
                        dockerImage.push()
                    }
                }
            }
        }
        
        stage('run') {
            steps {
                bat "docker run -d -p 8090:5000 salarabbas24/mlops_classtask:latest"
            }
        }
        
    }
}