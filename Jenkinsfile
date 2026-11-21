pipeline {
    agent any

    stages {
        stage('Stage 1'){
            steps{
                sh '''
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
                script{
                    // create a docker image
                    def image = docker.build("python-hello-app-image:${env.BUILD_NUMBER}")

                    // create, run and delete the container at the end
                    image.inside{
                        sh '''
                            echo "this is inside the hello-app container"
                            python --version
                            python app.py
                            echo "this is end of the hello-app container"
                        '''
                }

                sh '''
                    echo "this is inside of the agent container"
                    python3 --version
                '''
            }


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

    }

//     post {
//         always {
//             // delete the image(if created)
//             sh "docker rmi my-python-app:${env.BUILD_NUMBER} || true"
//         }
//     }
}
