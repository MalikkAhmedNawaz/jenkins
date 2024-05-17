pipeline {
   
    agent any
  environment{
     DOCKERHUB_CREDENTIALS=credentials('dockerhub-malikk611')
  }
    stages{
        stage('Build'){
            steps{
                sh 'npm install'

            }
        }
        stage('test'){
            steps{
                sh 'echo "Test is running"'
            }
        }
        stage('Docker build'){
            steps{
                sh 'docker build -t malikkahmednawaz786/jenkins-integration:latest .'
            }
        }
        stage('login'){
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push'){
            steps{
                sh 'docker push malikkahmednawaz786/jenkins-integration:latest'
            }
        }
        stage('deploy'){
            steps{
                sh 'echo "Deploying the application"'
            }
        }
      
    }




}
