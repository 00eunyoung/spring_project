pipeline {
    agent any
    
    tools {
        // Specify the name of the Git tool configured in Global Tool Configuration
        git 'https://github.com/00eunyoung/spring_project.git'
    }

    stages {
        stage('Checkout') {
            steps {
                // Git checkout step
                checkout scm
            }
        }
        
        stage('Prepare Gradle Wrapper') {
            steps {
                // Give execute permission to Gradle Wrapper script
                sh 'chmod +x ./gradlew'
            }
        }

        stage('Build') {
            steps {
                // Gradle build step
                sh './gradlew clean build'

            }
        }
        
        stage('Deploy to Tomcat') {
            steps {
                // Copy the WAR file to Tomcat's webapps directory
                sh 'cp build/libs/*.war /path/to/tomcat/webapps/'
            }
        }
    }
}
