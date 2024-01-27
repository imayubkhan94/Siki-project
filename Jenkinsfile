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
    }
}

