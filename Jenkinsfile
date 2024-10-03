pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the repository
                git url: 'https://github.com/Jigyansu1234/jenkins_pipeline_java_maven.git'
            }
        }

        stage('Build') {
            steps {
                // Get the Maven tool configured globally as 'M3'
                script {
                    // Make sure 'M3' is correctly configured in Jenkins
                    def mvnHome = tool name: 'M3' // Change 'M3' if your Maven installation has a different name
                    // Run the Maven build using the Maven tool path
                    sh "${mvnHome}/bin/mvn -Dmaven.test.failure.ignore clean package"
                }
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

