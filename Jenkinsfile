pipeline {
    agent {
        node {
            label 'maven'
        }
    }
environment {
    path= "/opt/apache-maven-3.9.4/bin:$PATH"
}

    stages {
        stage('build'){
          steps {
            sh 'mvn clean deploy'
          }
     
        }
    }

    stage('SonarQube analysis') {
    environment {
      scannerHome = tool 'valaxy-sonar-scanner
    }
      stpes {
        withSonarQubeEnv('My SonarQube Server') { // If you have configured more than one global server connection, you can specify its name
        sh "${scannerHome}/bin/sonar-scanner"}
    }   
}
}
