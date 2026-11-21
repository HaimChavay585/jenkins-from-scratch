pipeline {
    agent any

    stages {
        stage('Stage 1'){
            steps{
                sh '''
                    ls -la
                    echo "before touch"
                    touch stage_1.txt
                    echo "after touch"
                    ls -la
                '''
            }
        }

        stage('stage 2 - with a docker'){
            agent{
                docker{
                    image 'python:3.12-slim'
                }
            }
            steps{
                sh '''
                    ls -la
                    python3 --version
                    echo "before touch"
                    touch stage_2.txt
                    echo "after touch"
                    ls -la
                '''

            }
        }
//         stage('Build & Test Image') {
//             steps {
//                 script {
//                     // create a docker image
//                     def myImage = docker.build("my-python-app:${env.BUILD_NUMBER}")
//
//                     // create, run and delete the container at the end
//                     myImage.inside {
//                         sh '''
//                             echo "=== Starting container test ==="
//                             python --version
//                             python app.py
//                             echo "=== Container test finished ==="
//                         '''
//                     }
//                 }
//             }
//         }

        stage('Stage 3'){
            steps{
                sh '''
                    ls -la
                    echo "This is stage 3"
                    echo "before touch"
                    touch stage_3.txt
                    echo "after touch"
                    ls -la
                '''
            }
        }
    }

//     post {
//         always {
//             // delete the image(if created)
//             sh "docker rmi my-python-app:${env.BUILD_NUMBER} || true"
//         }
//     }
}
