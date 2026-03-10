pipeline {
    agent any

    tools {
        // Ensure these names match exactly what is configured 
        // in "Global Tool Configuration" in Jenkins
        maven "MAVEN"
        jdk "JDK"
    }

    stages {
        stage('Initialize') {
            steps {
                // On Windows, use 'bat' to print environment variables
                bat 'mvn -version'
                bat 'java -version'
            }
        }

        stage('Build') {
            steps {
                // Use relative paths from the root of the repository
                // If your pom.xml is in a subfolder called 'my-app':
                dir('my-app') {
                    bat "mvn -B -DskipTests clean package"
                }
            }
        }
    }

    post {
        always {
            // Standard Maven test result location is usually target/surefire-reports
            junit allowEmptyResults: true, testResults: '**/target/surefire-reports/*.xml'
        }
    }
}
