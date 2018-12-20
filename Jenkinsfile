

pipeline {
    /* A declarative Pipeline*/
    agent any
    stages{
        stage('Build'){
            steps {
                sh 'mvn clean pakage'           
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
/*        stage('Deploy to stagin'){
            /* agent section could go here as well*/
            steps {

            }
        }
    }
*/
}