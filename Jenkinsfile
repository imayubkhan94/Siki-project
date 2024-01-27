pipeline {
    agent any
tools{
    maven 'maven'
}
    stages {
        stage('Clone code') {
            steps {
               git 'https://github.com/imayubkhan94/Siki-project.git'
            }
        }
        
        stage('Build the code') {
            steps {
               sh 'mvn clean install'
            }
        }
         stage('Deploy to server') {
            steps {
            deploy adapters: [tomcat9(path: '', url: 'http://13.126.94.166:8080/')], contextPath: null, war: '**/*.war'            }
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
         stage('Docker registry') {
            steps {

withDockerRegistry(credentialsId: 'dockerid', url: 'https://hub.docker.com/') {
   
}

                
            }
        }
        
    }
}

