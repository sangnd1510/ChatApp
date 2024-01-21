pipeline {
    agent{
        any
    }
    stages{
        stage('building, deploying backend app'){
            steps{
                withDockerRegistry(credentialsId: 'dockerhub', url: 'https://index.docker.io/v1/'){
                    sh 'cd api'
                    sh 'docker compose up -d --build'
                    sh 'docker compose push'
                }
            }
        }
        stage('building, deploying frontend app'){
            steps{
                withDockerRegistry(credentialsId: 'dockerhub', url: 'https://index.docker.io/v1/'){
                    sh 'cd client'
                    sh 'docker compose up -d --build'
                    sh 'docker compose push'
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