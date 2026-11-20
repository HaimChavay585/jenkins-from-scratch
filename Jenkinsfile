pipeline {
    agent any

    stages {
        stage('Stage 1'){
            steps{
                sh '''
                    echo "This is stage 1"
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
                    echo "This is stage 3"
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
