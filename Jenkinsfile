pipeline {
    agent any
    tools {
        maven 'maven3'
    }
    stages {
        stage('Build') {
            steps {
                 sh script: 'mvn clean package'
            }
        }
        stage('Upload War to Nexus') {
            steps {
                 nexusArtifactUploader artifacts: [
                     [
                         artifactId: 'code-promo',
                         classifier: '', 
                         file: 'target/code-promo-1.0.0.war', 
                         type: 'war'
                    ]
                ], 
                credentialsId: 'nexus3',
                groupId: 'in.javahome',
                nexusUrl: 'new.nexusrepocodeprom.pagekite.me',
                nexusVersion: 'nexus2',
                protocol: 'http',
                repository: 'http://new.nexusrepocodeprom.pagekite.me/repository/code-promo/', 
                version: '1.0.0'
            }
        }
    }
}
