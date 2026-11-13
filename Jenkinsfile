
pipeline {
    agent any

    stages {

        stage('Git Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Moulali-Syed/sparkjava-war.git'
            }
        }

        stage('Check Java and Maven') {
            steps {
                sh 'java -version'
                sh 'mvn -version'
            }
        }

        stage('Build WAR') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Verify WAR') {
            steps {
                sh 'ls -lh target/*.war'
            }
        }

    }

    post {
        success {
            echo 'WAR generated successfully!'
        }

        failure {
            echo 'Build failed. Check the console output.'
        }
    }
}
