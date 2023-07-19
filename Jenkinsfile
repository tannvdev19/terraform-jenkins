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

    stages {
        stage('Check value') {
            steps {
                script {
                    String userInput = input(
                        id: 'userInput',
                        message: 'Do you want to proceed for production deployment?',
                        parameters: [
                            [$class: 'ChoiceParameterDefinition', choices: 'Confirm\nAbort', description: '', name: 'userInput']
                        ]
                    )
                    echo "User input: ${userInput}"
                    
                    if (userInput == 'Confirm') {
                        echo 'Proceeding with deployment'
                    } else {
                        error 'Aborting deployment'
                    }
                }
            }
        }
    }
}
