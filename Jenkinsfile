pipeline{
    agen any
    tools{
        maven 'M2_HOME'
    }
    stages{
        stage('maven build'){
            steps{
                sh mvn clean install package
            }
        }
            
    }
}