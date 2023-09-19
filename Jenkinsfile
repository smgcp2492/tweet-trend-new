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
environment {
    scannerHome = tool 'valaxy-sonar-scanner'
    }
      stage('SonarQube analysis') {
       stpes {
          withSonarQubeEnv('valaxy-sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
         sh "${scannerHome}/bin/sonar-scanner"
    }   
}
}
}
