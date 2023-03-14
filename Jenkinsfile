pipeline {
    agent any

    stages {
        stage('Git') {
            steps {heckout scmGit(branches: [[name: '*/master']], extensions: [cleanBeforeCheckout()], userRemoteConfigs: [[url: 'https://github.com/braemma2013/Jenkins-Project-2.git']])
                echo 'Checking out..'
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
            }  
        }
        stage('Test') {
            steps {
                echo 'Testing..'      
              
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
