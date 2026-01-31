pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build & Test') { 
            steps {
           
                sh '/opt/gradle-8.5/bin/gradle clean build'
            }
        }
        stage('Archive Artifact') { 
            steps {
                
                archiveArtifacts artifacts: 'build/libs/*.jar', fingerprint: true
            }
        }
	stage('SonarQube Analysis') {
            steps {
                sh '/opt/gradle-8.5/bin/gradle sonar'
            }
        }
    }
}
