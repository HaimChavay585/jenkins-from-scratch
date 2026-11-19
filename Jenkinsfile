pipeline {
    agent any

    stages {
        stage('Build & Test Image') {
            steps {
                script {
                    // create a docker image
                    def myImage = docker.build("my-python-app:${env.BUILD_NUMBER}")

                    // create, run and delete the container at the end
                    myImage.inside {
                        sh '''
                            echo "=== Starting container test ==="
                            python --version
                            python app.py
                            echo "=== Container test finished ==="
                        '''
                    }
                }
            }
        }
    }

    post {
        always {
            // delete the image(if created)
            sh "docker rmi my-python-app:${env.BUILD_NUMBER} || true"
        }
    }
}
