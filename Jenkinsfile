pipeline{
    agent any
    tools{
        maven 'M2_HOME'
    }
    stages{
        stage('maven build'){
            steps{
                sh 'mvn clean install package'
            }
            stage('upload artefact'){
                steps{
                    script{
                        def mavenpom = readMavenPom file: 'pom.xml'
                        nexusArtifactUploader artifacts:
                        [[artifactId: "${mavemPom.artifactid}",
                        classifier: '',
                        file: "target/${mavenPom.artifactId}-${mavenPom.version}.${mavenPom.packaging}",
                        type: "${mavenPom.packaging}"]]
                        credentialsId: 'NexusId',
                        groupId: "${mavenPom.groupId}",
                        nexusUrl: '18-232-173-173.compute-1.amazonaws.com:8081'   
                        protocol: 'http',
                        repository: 'geolocation',
                        version: "${mavenPom.version}"

                    }
                }
            }
        }
            
    }
}