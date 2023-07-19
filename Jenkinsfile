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

pipeline {
    agent any

    tools {
        terraform 'terraform'
    }

    environment {
        AWS_ACCESS_KEY_ID     = credentials('aws-secret-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('aws-secret-access-key')
    }

    stages {
        stage('Check value') {
            steps {
                script {
                    def userInput = input(
                        id: 'userInput',
                        message: 'Do you want to proceed for production deployment?',
                        parameters: [
                            [$class: 'SubmitterParameterDefinition', name: 'decision', value: 'Confirm', description: 'Click "Confirm" to proceed, or "Abort" to cancel.']
                        ]
                    )

                    if (userInput == 'Proceed') {
                        echo 'Proceeding with production deployment...'
                        // Your deployment steps go here, e.g., terraform apply -auto-approve
                        sh 'terraform apply -auto-approve'
                    } else {
                        echo 'Production deployment aborted.'
                    }
                }
            }
        }
    }
}
