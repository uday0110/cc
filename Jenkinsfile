pipeline {
    agent any
    parameters {
  file description: 'war file location', name: 'C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\Demo-Server1'
}
stages{
        stage("GIT checkout"){
            steps{
                git credentialsId: 'javahome2', url: 'https://github.com/uday0110/cc.git'
            }
        }
        stage('Upload War To Nexus') {
            steps {
                nexusArtifactUploader artifacts: [
                    [
                        artifactId: 'cc',
                        classifier: '',
                        file: "cc-1.0.war",
                        type: 'war'
                    ]
                ],
                credentialsId: 'nexus3',
                groupId: 'in.javahome',
                nexusUrl: '172.31.28.138:8081',
                nexusVersion: 'nexus3',
                protocol: 'http',
                repository: 'sample-releases',
                version: '1.0'
            }
        }
  stage('Deploy') {
    steps {
       deploy adapters: [tomcat9(credentialsId: '6778f56c-5efd-44a7-bd8e-9628cb499e7c', path: '', url: 'http://13.59.140.238:8080/')], contextPath: 'cc', war: 'cc.war' 
    }
}
}
}


