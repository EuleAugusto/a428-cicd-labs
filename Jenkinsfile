node {
    triggers {
        pollSCM('H/2 * * * *')
    }
    docker.image('node:16-buster-slim').inside('-p 3000:3000') {
        stage('Build') { 

                sh 'npm install' 

            }
        stage('Test') {
            
                sh './jenkins/scripts/test.sh'
            }
        stage('Deploy') {
                           
                sh './jenkins/scripts/deliver.sh'
                input message: 'Sudah selesai menggunakan React Apps? (Klik "Proceed" untuk mengakhiri)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }