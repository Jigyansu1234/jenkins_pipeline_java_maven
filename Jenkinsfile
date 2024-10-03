pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the repository
                git url: 'https://github.com/TTFHW/jenkins_pipeline_java_maven.git'
            }
        }

        stage('Build') {
            steps {
                // Get the Maven tool configured globally as 'M3'
                def mvnHome = tool 'M3'

                // Run the Maven build
                sh "${mvnHome}/bin/mvn -Dmaven.test.failure.ignore clean package"
            }
        }

        stage('Test Results') {
            steps {
                // Archive the test results using the junit step
                junit '**/target/surefire-reports/TEST-*.xml'
            }
        }
    }
}
