node {
    //scripted
 stage('Build') {
        docker.image('node:16-buster-slim').inside('-p 3000:3000') {
                sh 'npm install'
            }
        }
 stage('Test') {
        docker.image('node:16-buster-slim').inside('-p 3000:3000') {
                sh './jenkins/scripts/test.sh'
            }
        } 
 stage('Manual Approval') {
        docker.image('node:16-buster-slim').inside('-p 3000:3000') {
                input message: 'Lanjutkan ke tahap Deploy (klik "Proceed" untuk lanjut atau klik "Abort" untuk berhenti)'
            }
         }
 stage('Deploy') {
        docker.image('node:16-buster-slim').inside('-p 3000:3000') {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Sudah selesai menggunakan React Apps? (Klik "Proceed" untuk mengakhiri)'
                sleep(60)
                sh './jenkins/scripts/kill.sh'
            }
        }
 }