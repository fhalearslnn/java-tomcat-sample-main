pipeline {
    agent any
    stages {
        stage('Build Application') {
             steps{
                build job: 'build-web-app'
            }
        }
        stage('Deploy to Staging Environment'){
            steps{
                build job: 'deploy-app-staging-env'
            }            
        }
        stage('Deploy to Production Environment'){
            steps{
                timeout(time:5, unit:'DAYS'){
                    input message:'Approve PRODUCTION Deployment?'
                }
                build job: 'deploy-app-prod-env'
            }
        }
    }
}
