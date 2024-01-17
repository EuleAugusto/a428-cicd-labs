node {
    triggers {
        pollSCM('*/2 * * * *')
    }
    docker.image('node:16-buster-slim').inside('-p 3000:3000'){
    stage('Build') { 
                {
                sh 'npm install'
            }
        }
    stage('Test') {
            {
                //sh "chmod +x -R ${env.WORKSPACE}"
                sh './jenkins/scripts/test.sh'
            }
        }
 }
}