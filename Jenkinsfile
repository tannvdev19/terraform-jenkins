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
        stage('User Input') {
            steps {
                script {
                    // Define the options for the checkbox
                    def options = ['Option 1', 'Option 2', 'Option 3']

                    // Use the input step with checkboxParameter
                    def userChoice = input(
                        id: 'userInput',
                        message: 'Select one or more options:',
                        parameters: [
                            checkboxParameter(
                                name: 'UserChoice',
                                description: 'Choose options:',
                                checked: options // All options are initially checked
                            )
                        ]
                    )

                    echo "User's Choice: ${userChoice}"
                }
            }
        }
    }
}

