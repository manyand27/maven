pipeline {
    agent any

    tools {
        maven 'Maven'
        jdk 'JDK23'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/manyand27/maven.git',
                    credentialsId: 'github-token'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn package'
            }
        }

        stage('Run Application') {
            steps {
                bat 'mvn exec:java "-Dexec.mainClass=com.example.app.App"'
            }
        }
    }
}
