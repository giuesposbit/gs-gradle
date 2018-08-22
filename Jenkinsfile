pipeline {
    agent any
   
    stages {
        
            stage('Build') {
                steps {
                    dir ('complete') {
                        sh './gradlew clean build'
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
            always {
                dir ('complete') {
                    archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
                    junit 'build/test-results/**/*.xml'
                }
                echo 'One way or another, I have finished'
                deleteDir() /* clean up our workspace */
            }
    }
}
