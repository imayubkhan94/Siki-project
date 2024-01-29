pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = 'ayubkhan1555.dockerhub'
    }
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
            deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://3.109.210.126:8080/')], contextPath: null, war: '**/*.war'            }
        }
         stage('Docker image build') {
            steps {
             sh 'docker build -t myimage:1 .'
                sh 'ls -l'
                sh 'pwd'
                sh 'docker images'
                sh 'docker tag myimage:1 ayubkhan1555/dockerpractise:latest'
                sh  'docker images'
            }
        }
         stage('Docker registry') {
            steps {
            withDockerRegistry(credentialsId: 'dockerid', url: 'https://index.docker.io/v1/') {
   
}

                
            }
        }
         
        stage('Docker push Image') {
          steps {
            sh  docker.withRegistry('https://index.docker.io/v1/', 'dockerid') {
            docker.image("ayubkhan1555/dockerpractise:latest").push()
    }
}

    }
}
}

