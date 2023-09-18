pipeline {
    agent {
        node {
            label 'maven'
        }
    }

    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/smgcp2492/tweet-trend-new.git'
            }
        }
    }
}