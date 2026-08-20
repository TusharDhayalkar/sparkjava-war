pipeline {
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
        stage('build') { 
            steps {
                sh 'mvn clean package'
            }
    }

    stages ('SonarQube analysis') {
        environment {
            scannerHome = tool ; 'SonarQube Scanner'
      
        }

        steps {
            withSonarQubeEnv( 'Sonar-Qube Server') {

                sh "${scannerHome}/bin/sonar-scanner"
         
            }
         }
      }
   }
}


