pipeline {
    agent any
    
    parameters {
        booleanParam(defaultValue: true, description: '', name: 'workingDir')
    }
    
    stages {
        dir ('complete') {
            stage('Build') {
                steps {
                    sh './gradlew build'
                }
            }
            stage('Test') {
                steps {
                    sh './gradlew check'
                }
            }
        }
    }

    post {
        dir ('complete') {
            always {
                archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
                junit 'build/reports/**/*.xml'
            }
        }
    }
}
