pipeline {
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }

    stages {

        stage("build") {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('SonarQube Analysis') {
            environment {
                 scanner_Home = tool 'tusharsonar'

            }

            steps {
                withSonarQubeEnv('tushar-sonarqube-server') {

                    sh "${SCANNER_HOME}/bin/sonar-scanner"

                }
            }
       }
    }
}
