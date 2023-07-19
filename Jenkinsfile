// pipeline {
//     agent any

//     tools {
//         terraform 'terraform'
//     }

//     environment {
//         AWS_ACCESS_KEY_ID     = credentials('aws-secret-key-id')
//         AWS_SECRET_ACCESS_KEY = credentials('aws-secret-access-key')
//     }

//     stages {
//         stage('Init Provider') {
//             steps {
//                 sh 'terraform init'
//             }
//         }
//         stage('Plan Resources') {
//             steps {
//                 sh 'terraform plan'
//             }
//         }
//         stage('Apply Resources') {
//             input {
//                 message 'Do you want to proceed for production deployment?'
//             }
//             steps {
//                 sh 'terraform apply -auto-approve'
//             }

//         }
//     }
// }

def firstName = null
pipeline {
    agent none
    stages {
        stage('input') {
            steps {
                script {
                    firstName = input(
            message: 'What is your first name?',
            ok: 'Submit',
            
            parameters: [string(defaultValue: 'Dave', name: 'FIRST_NAME', trim: true)]
          )
                }
            }
        }
        stage('output') {
            agent any
            steps {
                script {
                    echo "Good Morning, $firstName"
                }
                sh '''
          hostname
          cat /etc/redhat-release
        '''
            }
        }
    }
}
