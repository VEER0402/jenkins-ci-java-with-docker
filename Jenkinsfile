pipeline {
    agent {
        docker {
            image 'maven:3.9.9-eclipse-temurin-17'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }

    stages {
        stage('Build inside Docker') {
            steps {
                sh 'mvn clean package'
            }
        }
    }

    post {
        success {
            echo 'Docker-based Maven build SUCCESS'
        }
        failure {
            echo 'Docker-based Maven build FAILED'
        }
    }
}

