pipeline {
    agent any

    stages {
        stage('Maven Build') {
            steps {
                //for windows machine
               // bat 'mvn clean package'
                //for linux machine
                sh 'mvn clean package'
            }
            post{
                success{
                    echo 'Archiving the project...'

                    archiveArtifacts artifacts : '**/*.war'
                }
            }
        }
        stage('Building Docker Image'){
            steps{

                sh "docker build . -t tomcatwebapp:${env.BUILD_ID}"
            }
        }
        
    }
}