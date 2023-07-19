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

    environment {
        boolean isProceed = false
    }
    stages {
        stage('User Input') {
            steps {
                script {
                    // Use the input step with checkBox parameter
                    try {
                        userChoice = input(
                            id: 'userInput',
                            message: 'Select one or more options:'
                        )
                        env.isProceed = true
                    } catch (err) {
                        echo 'User chose to abort the build.'
                        env.isProceed = false
                        error 'Build aborted by user.'
                    }

                // Add more echos or use the selected options in your pipeline logic
                }
            }
        }

        stage('Next Steps') {
            steps {
                script {
                    echo "User choice was: ${env.isProceed}"
                }
            }
        }
    }
}
