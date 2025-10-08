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
        stage('Scan'){
            steps{
                withSonarQubeEnv(installationName:'SonarQube'){
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
