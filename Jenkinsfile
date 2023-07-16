pipeline {
    agent any
    
    environment {
        SONARQUBE_HOME = tool 'sonarscanner'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Shahid199578/sonarqube_integration_with_jenkins.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                sh 'mvn sonar:sonar \
                    -Dsonar.projectKey=Jeninks_Sonar \
                    -Dsonar.host.url=http://54.92.169.135:9000 \
                    -Dsonar.login=14da92f285c610f98780db44e07c81f6883405d7'
            }
        }
    }

    post {
        always {
            deleteDir()
        }
    }
}
