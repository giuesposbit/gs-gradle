pipeline {
    agent any
    
    parameters {
        booleanParam(defaultValue: true, description: '', name: 'workingDir')
    }
    
    stages {
        
            stage('Build') {
                steps {
                    dir ('complete') {
                        sh './gradlew build'
                    }
                }
            }
            stage('Test') {
                steps {
                    dir ('complete') {
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
