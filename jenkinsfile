pipeline {
    agent any
    tools {
        maven "Maven"
    }
    stages {
        stage ("Clone code from VCS") {
            steps {
                    git 'https://github.com/avinashneworg/simple-app.git';
                }
            }
        stage("Maven Build") {
            steps {
                 sh 'mvn clean package'
                }
            }
        stage("Upload artifact to Nexus Repository") {
            steps {
                nexusArtifactUploader artifacts: [
                    [
                        artifactId: 'simple-app', 
                        classifier: '', 
                        file: 'target/simple-app-3.0.0.war', 
                        type: 'war'
                    ]
               ], 
               credentialsId: 'nexus3', 
               groupId: 'in.javahome', 
               nexusUrl: '172.31.33.162:8081', 
               nexusVersion: 'nexus3', 
               protocol: 'http', 
               repository: 'nexusrepo', 
               version: '3.0.0'
           }
       }
    }
}
