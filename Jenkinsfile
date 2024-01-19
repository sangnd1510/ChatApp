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
    }
}