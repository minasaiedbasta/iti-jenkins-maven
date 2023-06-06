pipeline {
    agent any
    
    stages {
        stage('Build and Push Docker Image') {
            when {
                branch 'release'
            }
            steps {
                echo 'Build and push the Docker image'
            }
        }
        
        stage('Deploy Docker Image') {
            when {
                branch 'dev' || branch 'test' || branch 'prod'
            }
            steps {
                echo 'Deploy the released Docker image'
            }
        }
    }
}
