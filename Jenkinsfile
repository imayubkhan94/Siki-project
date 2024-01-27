pipeline {
    agent any
tools{
    maven 'maven'
}
    stages {
        stage('Clone code') {
            steps {
               git 'https://github.com/SikindharBasha/Siki-project.git'
            }
        }
        
        stage('Build the code') {
            steps {
               sh 'mvn clean install'
            }
        }
         stage('Deploy to server') {
            steps {
              deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://3.7.253.112:8081/')], contextPath: null, war: '**/*.war'
            }
        }
         stage('Docker image build') {
            steps {
             sh 'docker build -t myimage:1 .'
                sh 'ls -l'
                sh 'pwd'
                sh 'docker images'
                sh 'docker tag myimage:1 sikindharbasha/myapplication:shafil2'
                sh  'docker images'
            }
        }
        
    }
}

