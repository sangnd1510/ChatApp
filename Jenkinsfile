pipeline {
    agent any
    stages{
        stage('building, deploying backend app'){
            steps{
                withDockerRegistry(credentialsId: 'dockerhub', url: 'https://index.docker.io/v1/'){
                    sh 'docker compose -f api/compose.yaml up -d --build'
                    sh 'docker compose -f api/compose.yaml  push'
                }
            }
        }
        
        stage('building, deploying frontend app'){
            steps{
                withDockerRegistry(credentialsId: 'dockerhub', url: 'https://index.docker.io/v1/'){
                    sh 'docker compose -f client/compose.yaml up -d --build'
                    sh 'docker compose -f client/compose.yaml push'
                }
            }
        }
    }
    post{
        always{
            cleanWs()
        }
    }
}