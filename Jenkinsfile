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
                    image 'docker:cli'
                }
            }
            steps{
                script{
                    sh '''
                        echo "inside script"
                        python app.py
                    '''

//                     // create a docker image
//                     def image = docker.build("python-hello-app-image:${env.BUILD_NUMBER}")
//
//                     // create, run and delete the container at the end
//                     image.inside{
//                         sh '''
//                             echo "this is inside the hello-app container"
//                             python --version
//                             python app.py
//                             echo "this is end of the hello-app container"
//                         '''
//                     }
                }
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
