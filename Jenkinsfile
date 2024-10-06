pipeline
{
    agent any
    environment
    {
        registry='sundarrajboobalan/repo1'
        dockerImage=''   
         registryCredential ='dockerhub-id'
        }
    stages
    {
        stage('checkout')
        {
            steps
            {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sundarrajboobalan/demoapp.git']])
            }
        
            
        }
        
        stage('Build docker image')
        {
            steps
            {
                script
                {
                    dockerImage = docker.build registry
                }
            }
        }
    stage('Push docker image')
{
    steps
    {
        script
        {
            docker.withRegistry( '', registryCredential ) 
            {
            dockerImage.push()
        }
    }
}        
    }
    }
}
