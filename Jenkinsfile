pipeline {
    agent any
    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
                sh "docker build . -t tomcatwebapp:${env.BUILD_ID}"
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    }
}
