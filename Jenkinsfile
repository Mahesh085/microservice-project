pipeline {
    agent any

    stages {
        stage('Docker build') {
            steps {
                sh "docker build -t umamahesh085/checkoutservice:v1 ."
            }
        }
        stage('Docker push') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'Docker-CRED') {
                       sh "docker push umamahesh085/checkoutservice:v1" 
                    }
                }
            }
        }
    }
}
