
pipeline {
    agent any

    environment {
        PATH = "/opt/maven/bin:${env.PATH}"
    }

    stages {

        stage('Check Java and Maven') {
            steps {
                sh 'java -version'
                sh 'mvn -version'
                sh 'which mvn'
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
            echo 'Build failed. Check console output.'
        }
    }
}
