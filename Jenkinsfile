pipeline {
    agent any
    
    parameters {
        string(name: 'workingDir', defaultValue: 'complete', description: 'La deirectory del repository in cui c\'e il sorgente')
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
