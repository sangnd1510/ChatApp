pipeline{
    agent any
    tools{
        nodejs my-node
    }
    stages{
        stage('build backend app'){
            steps{
                echo 'build backend app'
                sh 'cd ./api && npm install && npm run build'
            }

        }
        stage('build client app'){
            steps{
                echo 'build client app'
                sh 'cd ./client && npm install && npm run build'
            }
        }
        stage('pushing backend image'){
            steps{
                withDockerRegistry(credentialsId: 'dockerhub', url: 'https://index.docker.io/v1/')
                echo 'pushing image'
                sh 'cd api && docker compose push'
                sh 'cd client && docker compose push'
            }
        }
        stage('Deploy server to DEV'){
            steps{
                echo 'Deploying'
                sh 'cd ./api && docker compose up --build'
            }
        }
        stage('Deploy client to DEV'){
            steps{
                echo 'Deploying'
                sh 'cd ./api && docker compose up --build'
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}