pipeline {
    agent any

    stages {
        stage('Testing Maven') {
            steps {
                sh 'mvn -version'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install -DskipTests'
            }
        }

        stage('Build & Sonar') {
            steps {
                sh 'chmod +x mvnw'
                withCredentials([string(credentialsId: 'jenkins-sonar', variable: 'sqa_8dca27735bed35feb2e9bab16ad07a2bf7c92dc8')]) {
                sh './mvnw org.sonarsource.scanner.maven:sonar-maven-plugin:3.9.0.2155:sonar -Dsonar.login=sqa_8dca27735bed35feb2e9bab16ad07a2bf7c92dc8'
            }
            }
        }


        stage('Tests') {
            steps {
                sh 'mvn test'
            }
        }
    }
}
