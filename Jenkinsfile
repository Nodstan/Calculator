pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Nodstan/Calculator.git'
            }
        }

        stage('Compile') {
            steps {
                bat 'mvn clean compile'
            }
        }

        stage('Unit test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Code coverage') {
            steps {
                bat 'mvn jacoco:report'

                publishHTML(target: [
                    reportDir: 'target/site/jacoco',
                    reportFiles: 'index.html',
                    reportName: 'JaCoCo Report'
                ])

                bat 'mvn jacoco:check'
            }
        }
    }
}
