pipeline {
    agent any

    tools {
        maven "MAVEN"
        jdk "JDK"
    }

    stages {

        stage('Initialize') {
            steps {
                echo "PATH = ${M2_HOME}\\bin;${PATH}"
                echo "M2_HOME = C:\\Program Files\\Apache\\Maven"
            }
        }

        stage('Build') {
            steps {
                dir("C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\demopipelinetask\\my-app") {
                    bat "mvn -B -DskipTests clean package"
                }
            }
        }
    }

    post {
        always {
            junit(
                allowEmptyResults: true,
                testResults: '**/test-reports/*.xml'
            )
        }
    }
}
