pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Git checkout step with Git tool named "Default"
                git tool: 'Default', url: 'https://github.com/00eunyoung/spring_project.git'
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
                // Gradle clean and build
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
