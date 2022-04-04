pipeline {
    // Where to execute like agent/node
    agent any

    stages {

        stage("build") {

            steps {
                sh '''
                    #!/bin/bash
                    echo "building app..."
                    systemctl show --property ActiveState docker | grep inactive
                    ACTIVESTATE=$(echo $?)

                    if [ $ACTIVESTATE != 0 ]
                    then
                    echo "Docker is in active state!"
                    else 
                    echo "Starting docker..."
                    service docker start
                    echo "Docker has been started!"
                    fi

                    echo "Building image..."
                    IMAGE=mathi12/resume
                    TAG=2.0
                    docker build -t $IMAGE:$TAG /mnt/c/Users/Lenovo/Desktop/website
                    echo "Image has been successfully built."
                '''
            }
        }

        stage("test") {

            steps {
                echo "testing app..."
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
