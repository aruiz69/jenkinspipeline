

pipeline {
    /* A declarative Pipeline*/
    agent any
    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'           
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to Staging'){
            steps{
                build job: 'PipeLine-Deploy-to-Stagin'
            }
        }
        stage ('Deploy to production'){
            steps{
                timeout(time:5, unit:'DAYS'){
                    input message:'Approve PRODUCTION Deployment'
                }

                build job: 'Pipeline-Deploy-to-Prod'
            }
            post {
                success {
                    echo 'Code deployed to production'
                }

                failure {
                    echo 'Deployment failed, try again'
                }
            }
        }
    }
}