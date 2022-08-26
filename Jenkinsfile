pipeline{
    agent any
    environment {
        PATH = "/opt/maven/apache-maven-3.8.6/bin:$PATH"
    }
    stages {
        stage ('checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/gourip092/testrepoformyproject.git'
                
            }
        }
        stage ('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage ('Nexus Upload') {
            steps {
                nexusArtifactUploader artifacts: [
                    [
                        artifactId: 'trucks', 
                        classifier: '', 
                        file: 'target/trucks.war', 
                        type: 'war'
                    ]
                    
                ], credentialsId: 'nexus3',
                groupId: 'com.companyname.automobile', 
                nexusUrl: '52.66.152.193:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'sampleapp-release', 
                version: '1.0.3'
            }
        }
    }
}
