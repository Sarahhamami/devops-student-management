pipeline{
    agent any
    stages{
        stage('Testing Maven'){
            steps{
                sh 'mvn -version'
            }
        }
        stage ('Build'){
            steps{
                sh 'mvn clean install -DskipTests'
            }
        }
        stage('Build & Sonar') {
            steps {
                // Ensure mvnw is executable
                sh 'chmod +x mvnw'

                // Run Maven build + Sonar
                sh './mvnw clean org.sonarsource.scanner.maven:sonar-maven-plugin:3.9.0.2155:sonar'
            }
        }

        }
        stage('Tests'){
            steps{
                sh 'mvn test'
            }
        }
    }
}
