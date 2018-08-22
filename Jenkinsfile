pipeline {
    agent any
    
    parameters {
        booleanParam(defaultValue: 'complete', description: '', name: 'workingDir')
    }
    
    stages {
        
            stage('Build') {
                steps {
                    dir ('${params.workingDir}') {
                        sh './gradlew build'
                    }
                }
            }
            stage('Test') {
                steps {
                    dir ('${params.workingDir}') {
                        sh './gradlew check'
                    }
                }
            }
        
    }

    post {
        
            always {
                dir ('${params.workingDir}') {
                    archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
                    junit 'build/reports/**/*.xml'
                }
            }
        
    }
}
