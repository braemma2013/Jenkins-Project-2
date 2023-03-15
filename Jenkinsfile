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
            steps {deploy adapters: [tomcat8(credentialsId: '1807e5e2-a89a-464f-81d9-ad11bef435d6', path: '', url: 'http://34.234.204.122:8080/')], contextPath: null, war: '**/*.war'
                echo 'Deploying....'
            }
        }
    }
}
