pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                sh 'mvn -f pom.xml clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: '**/*.war'
                }
       
            }
        }

            stage('create Tomcat Docker Image'){
                steps {
                    sh "pwd"
                    sh "ls -a"
                steps {
                    sh "docker build . -t tomcatsamplewebapp:${env.BUILD_ID}"
                }
            }      

    }
}
