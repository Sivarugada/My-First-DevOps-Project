pipeline {
    agent any

    tools {
        maven 'M3' 
    }

    stages {
        stage('Checkout') {
            steps {
                // This uses the credentials you just configured in the UI
                checkout scm
            }
        }
    }
}
