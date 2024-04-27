pipeline {
    agent any   //add label if you want remote docker
    
    stages {
        stage('Git Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/rndudhe1808/Docker.git'        
            }
        }
        
        stage('Docker build') {
            steps {
                sh 'docker build -t ram1808/dockerjenkins:$BUILD_NUMBER .' 
            }
        }
        
        stage('Docker push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockercred') {
                        sh 'docker push ram1808/dockerjenkins:$BUILD_NUMBER'
                    }
                }
            }
        }     
        stage('Docker run') {
            steps {
                script {
                    sh 'docker run -d ram1808/dockerjenkins:$BUILD_NUMBER'
                    
                }
            }
        } 
    }
}
