pipeline {
    agent any
    tools{
      maven 'Maven'
    }    
    stages {
        stage('Git') {
            steps {checkout scmGit(branches: [[name: '*/main']], extensions: [cleanBeforeCheckout()], userRemoteConfigs: [[url: 'https://github.com/braemma2013/Jenkins-Project-2.git']])
                echo 'Checking out..'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install -f JavaWebCalculator-master/pom.xml'
            }  
        }
        stage('Test') {
            steps {
                sh 'junit 'myproject/target/test-reports/*.xml''   
              
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
