pipeline {
    agent any 
    
    tools {
        maven 'mymaven'
    }
    
    stages {
        stage('Clonerepo') {
            steps {
                git 'https://github.com/bhasker-manikyala/DevOpsClassCodes.git'
            }
        }
        stage('Compile') {
            steps {
                sh 'mvn compile'
            }
        }
        stage(Code Review) {
            steps {
                sh 'mvn pmd:pmd'
            }
        }
        stage(Unit Testing){
            steps {
                sh 'mvn test'
            }
        }
        stage('Codecoverage'){
            steps {
               sh 'mvn verify'   
            }
        }
        stage('Package'){
            steps {
               sh 'mvn package'   
            }
        stage('SonarQube Analysis') {
    def mvn = tool 'Default Maven';
    withSonarQubeEnv() {
      sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=ecocode"
    } }
        }
    }
}
