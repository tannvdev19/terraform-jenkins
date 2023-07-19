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
        stage('User Input') {
            steps {
                script {
                    // Use the input step with checkBox parameter
                    def userChoice
                    try {
                        userChoice = input(
                            id: 'userInput',
                            message: 'Select one or more options:'
                        )
                        currentBuild.result = 'PROCEED'
                    } catch (err) {
                        echo 'User chose to abort the build.'
                        currentBuild.result = 'ABORTED'
                        error 'Build aborted by user.'
                    }
                    echo "User's Choice - Option 1: ${userChoice.Option1}"
                    echo "User's Choice - Option 2: ${userChoice.Option2}"
                // Add more echos or use the selected options in your pipeline logic
                }
            }
        }

        stage('Next Steps') {
            steps {
                script {
                    echo "User choice was: ${currentBuild.result}"
                }
            }
        }
    }
}
