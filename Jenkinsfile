#!/usr/bin/env groovy
pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage("Build jar App") {
            steps {
                script {
                    echo "building application..."
                    sh "mvn package"
                }
            }
        }
        stage("Build Docker Image") {
            steps {
                when {
                    expression {
                        branch 'release'
                    }
                }
                script {
                    echo "building docker image..."
                    withCredentials ([usernamePassword(credentialsId:'dockerhub',usernameVariable: 'USER',passwordVariable:'PASS')]) {
                        sh "docker build -t minasaiedbasta/demo-maven-app:jma-3.0 ."
                        sh 'echo $PASS | docker login -u $USER --password-stdin'
                        sh "docker push minasaiedbasta/demo-maven-app:jma-3.0"
                    }
                }
            }
        }
        stage("Deploy Image") {
            steps {
                when {
                    expression {
                        branch 'dev', 'test', 'prod'
                    }
                }
                script {
                    echo "deploying application..."
                }
            }
        }
    }
}