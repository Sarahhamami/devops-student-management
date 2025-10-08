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
                sh 'mvn clean install'
            }
        }
        stage('SonarQube Analysis'){
            steps{
                withSonarQubeEnv('SonarQube'){
                    sh 'mvn run sonar'
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
