pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                sh './complete/gradlew check'
            }
        }
    }
    post {
        always {
            junit './complete/build/test-results/*.xml'
        }
    }
}
