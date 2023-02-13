#!/usr/bin/env groovy
pipeline {
    agent any

    stages {
        stage('CloneRepo') {
            steps {
                git branch: 'main', credentialsId: 'admin', url: 'https://github.com/amiya77/Micro-Service.git'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t build-project1 .'
            }
        }
        
        stage('Tag') {
            steps {
                sh 'docker tag build-project1 amiya777/build-project1'
                sh 'docker push amiya777/build-project1'
            } 
        }
        stage('Run') {
            steps {
                sh 'docker run -d -p 80:8000 build-project1:latest'
            }
        }
    }
}
