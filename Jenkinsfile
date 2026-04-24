pipeline {
    agent any
    
    tools{
         maven "maven-3.9.15"
    }
    stages {
        stage('clone') {
            steps {
              git 'https://github.com/amarkrbelur-ai/maven-web-app.git'
            }
        }
        stage('build'){
            steps{
                 sh 'mvn clean package'
            }
        }
        stage('docker image'){
            steps {
                sh 'docker build -t amar/mavenwebapp .'
            }
        }
        stage('k8s deploy'){
            steps{
               sh 'kubectl apply -f k8s-deploy.yml'
            }
        }
    }
}
