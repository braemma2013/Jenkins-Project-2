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
                 junit allowEmptyResults: true, testResults: '**/test-reports/*.xml'   
              
            }
        }
        stage('Deploy') {
            steps {deploy adapters: [tomcat9(credentialsId: '6698b1be-a3e3-424a-ac28-20f967fe440b', path: '', url: 'http://44.203.16.195:8080/')], contextPath: null, war: '**/*.war'
                echo 'Deploying....'
            }
        }
    }
}
