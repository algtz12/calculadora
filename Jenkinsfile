pipeline {
    agent any
    triggers { cron('H */4 * * 1-5') }
    stages {
        stage('build') {
            steps {
                bat 'gradle clean build -x test'
            }
        }
        stage('test') {
            steps {
                bat 'gradle test'
            }
        }
        stage('sonar') {
            steps {
                def scannerHome = tool 'SonarQube 3.2';
                withSonarQubeEnv('My SonarQube Server') {
                      bat "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}