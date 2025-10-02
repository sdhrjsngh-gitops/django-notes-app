@Library("Shared") _
pipeline {
    agent any

    stages {
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage('Code') {
            steps {
                script{
                clone("https://github.com/sdhrjsngh-gitops/django-notes-app.git", "main")
                }
            }
        }
        stage('Build') {
            steps {
                script{
                docker_build("notes-app", "latest", "imdhrjsngh") 
                }
            }
        }
        stage('Push to DockerHub') {
            steps {
                script{
                    docker_push("notes-app", "latest", "imdhrjsngh")
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'This is deploying the code'
                sh "docker-compose up -d"
            }
        }
    }
}
