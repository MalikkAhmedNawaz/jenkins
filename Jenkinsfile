pipeline {
    agent {
        docker {
            image 'node:14'
            label 'docker'
        }
    }
    stages {
        stage('Build') {
            steps {
                script {
                    def app = docker.build("malikkahmednawaz786/my-app:${env.BUILD_ID}")
                    app.inside {
                        sh 'npm install'
                    }
                }
            }
        }
        stage('Test') {
            steps {
                sh 'echo "No tests implemented yet"'
            }
        }
        stage('Push to DockerHub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-malikk611') {
                        def app = docker.build("malikkahmednawaz786/my-app:${env.BUILD_ID}")
                        app.push()
                    }
                }
            }
        }
    }
}
