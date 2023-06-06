#!/usr/bin/env groovy
@Library('jenkins-shared-library')_
pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage("build jar") {
            steps {
                script {
                    buildJar()
                }
            }
        }
        stage("build image") {
            steps {
                script {
                    buildImage 'minasaiedbasta/demo-maven-app:jma-3.0'
                }
            }
        }
        stage("deploy") {
            steps {
                script {
                    echo "deploying application..."
                }
            }
        }
    }
}