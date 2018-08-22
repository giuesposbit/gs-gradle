pipeline {
    agent any
    
    dir ('complete') {
        stages {
            stage('Test') {
                steps {
                    sh './gradlew check'
                }
            }
        }
        post {
            always {
                junit 'build/test-results/**/*.xml' 
            }
        }
    }

}
