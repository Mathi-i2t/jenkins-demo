pipeline {
    // Where to execute like agent/node
    agent any

    stages {

        stage("build") {

            steps {
                sh '''
                    #!/bin/bash
                    echo "building app..."
                   
                    echo "Starting docker..."

                    echo "Building image..."
                    IMAGE=mathi12/resume
                    TAG=2.0
                    cd
                    cd Desktop/website
                    docker build -t $IMAGE:$TAG .
                    echo "Image has been successfully built."
                '''
            }
        }

        stage("test") {

            steps {
                echo "testing app!"
            }
        }
        
        stage("deploy") {

            steps {
                sh '''
                echo "deploying app..."
                docker run -d -p 8000:80 mathi12/resume:2.0
                '''
            }
        }
    }
    
}
