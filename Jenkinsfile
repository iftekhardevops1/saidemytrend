pipeline {
    agent any 
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }

    stages {
        stage ('Build') {
            steps {
                sh 'mvn clean deploy'
            }
        }
        stage ('Sonarqube Analysis') {
            environment {
                scannerHome = tool 'saidemy-sonar-scanner'
            }
            steps {
                with SonarQubeEnv('saidemy-sonarqube-server') {
                    sh "${scannerhome}/bin/sonar-scanner"
                }
            }
            
        }
    }
    
}
