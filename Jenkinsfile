pipeline {
    agent any
    
    stages {
        
        stage('Get Code') {
            steps {
               git branch: 'main', changelog: false, credentialsId: 'gitsecret', poll: false, url: 'https://github.com/akaspatranobis/my-simple-docker-ci-cd-pipeline-project.git'
            }
        }
        # Stage 2
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('nginx:v1')
                }
            }
        }

        # Stage 3
        stage('Run Container') {
            steps {
                script {
                    def customContainerName = 'nginx'
                    def portMappings = '8082:80' // Format: hostPort:containerPort
                    docker.image('nginx:v1').run("-p ${portMappings} --name ${customContainerName}")
                }
            }
        }
    }
}