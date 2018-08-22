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
                //mail to: 'serbo83@gmail.com', subject: "Pipeline: ${currentBuild.fullDisplayName}", body: "Build: ${env.BUILD_URL}"
                dir ('complete') {
                    archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
                    junit 'build/test-results/**/*.xml'
                }
                echo 'One way or another, I have finished'
                deleteDir() /* clean up our workspace */
            }
    }
}
