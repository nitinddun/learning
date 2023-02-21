pipeline {
    agent any

    stages {
        stage('Docker Build') {
            steps {
                sh '''
                git pull git@github.com:nitinddun/learning.git main
                sudo docker build -t 767243193153.dkr.ecr.ap-northeast-1.amazonaws.com/pipeline:$BUILD_NUMBER .
                # login to ecr 
                aws ecr get-login-password --region ap-northeast-1 | docker login --username AWS --password-stdin 767243193153.dkr.ecr.ap-northeast-1.amazonaws.com
                #push the image to ecr 
                docker push 767243193153.dkr.ecr.ap-northeast-1.amazonaws.com/pipeline:$BUILD_NUMBER
                '''
            }
        }
        // stage('EKS Deploy') {
        //     steps {
        //         sh '''
        //         # helm 
        //         helm upgrade -i static-dev static -n dev --set image.tag=$BUILD_NUMBER
        //         '''

            }
        }
    
