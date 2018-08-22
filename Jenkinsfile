pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                dir ('complete') {
                    sh './gradlew check'
                }
            }
        }
    }
    post {
        always {
            dir ('complete') {
                junit './complete/build/test-results/*.xml'
            }
        }
    }
}
