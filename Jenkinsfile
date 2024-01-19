pipeline{
    agent any
    tools{
        nodejs 'my-node'
    }
    stages{
        stage('build backend app'){
            steps{
                echo 'build backend app'
                sh 'cd ./api && yarn install && yarn run build'
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