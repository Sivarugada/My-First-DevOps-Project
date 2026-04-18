pipeline {
    agent any

    tools {
        // This must match the name you gave in Global Tool Configuration
        maven 'M3' 
    }

    stages {
        stage('Cleanup') {
            steps {
                echo 'Cleaning up workspace...'
                cleanWs()
            }
        }

        stage('Checkout SCM') {
            steps {
                // 'checkout scm' is the standard way to pull from the repo 
                // linked to the job.
                checkout scm
            }
        }

        stage('Git Checkout') {
            steps {
                // If you specifically need to checkout a different branch manually:
                git branch: 'main', url: 'https://github.com/your-username/your-repo.git'
            }
        }

        stage('Unit Test') {
            steps {
                echo 'Running Maven Unit Tests...'
                // -B runs in non-interactive (batch) mode
                sh 'mvn -B test'
            }
            post {
                always {
                    // This captures the test results for the Jenkins UI
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }
        
        stage('Package') {
            steps {
                sh 'mvn -B package -DskipTests'
            }
        }
    }
}
