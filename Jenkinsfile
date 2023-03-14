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
            steps {deploy adapters: [tomcat9(credentialsId: 'bbf7b10b-5267-4e7e-add2-c44ca7587718', path: '', url: 'http://3.94.150.36:8080/')], contextPath: null, war: '**/*.war'
                echo 'Deploying....'
            }
        }
    }
}
