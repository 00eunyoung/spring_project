pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Git checkout step
                checkout master
            }
        }
        
        stage('Build') {
            steps {
                // Gradle build step
                sh './gradlew build'
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
