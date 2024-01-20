ipeline {
    agent {
        docker {
            image 'node:16-buster-slim' 
            args '-p 3000:3000' 
        }
    }
    triggers {
        pollSCM('*/2 * * * *')
    }
    
    stage {
        ('Build') { 
            steps {
                sh 'npm install' 
            }
        }
       ('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
       ('Deploy') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Sudah selesai menggunakan React Apps? (Klik "Proceed" untuk mengakhiri)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}