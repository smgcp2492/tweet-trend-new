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
            echo "----- build started -----"
            sh 'mvn clean deploy -Dmaven.test.skip=true'
            echo "----- build Completed ----"
          }
        }
       stage ('unit test'){
          steps{
            echo"---- unit test started----"
            sh 'mvn surefire-report:report'
             echo "--------unit test Completed----"
          }
       }
      
    stage('SonarQube analysis') {
    environment {
      scannerHome = tool 'valaxy-sonar-scanner'
    }
    steps{
    withSonarQubeEnv('valaxy-sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
      sh "${scannerHome}/bin/sonar-scanner"
    }
    }
  }
}
}
