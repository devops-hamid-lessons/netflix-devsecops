#! /usr/bin/env groovy

//test branch
@Library("jenkinsSharedLib")
def gv
pipeline {
    agent any

//    tools {
//        maven 'Maven'
//    }

    environment {
        IMAGE_NAME = "grahamtty/netflix"
        IMAGE_VERSION = "latest"
        AWS_ACCESS_KEY_ID = credentials('aws_access_key_id') //this is like exporting params. so it is enough to automatically login aws.
        AWS_SECRET_ACCESS_KEY = credentials("aws_secret_access_key")
    }
    stages {

//        stage("build jar") {
//            steps {
//                echo "building the application..."
//                sh 'mvn clean package'
//            }
//        }

//        stage("Docker Build & Push"){
//            steps{
//                script{
//                    withCredentials([usernamePassword(credentialsId: 'dockercredit', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
//                        sh "echo ${env.PASS} | docker login -u ${env.USER} --password-stdin "
//                        sh "docker build --build-arg TMDB_V3_API_KEY=0285a5a87919af58f3df89de4348255f  -t ${env.IMAGE_NAME}:${env.IMAGE_VERSION} ."
//                        sh "docker push ${env.IMAGE_NAME}:${env.IMAGE_VERSION}"
//                    }
//                }
//            }
//        }

//        stage("provision dev env"){
//            environment {
//                AWS_ACCESS_KEY_ID = credentials('aws_access_key_id') //this is like exporting params. so it is enough to automatically login aws.
//                AWS_SECRET_ACCESS_KEY = credentials("aws_secret_access_key")
//            }
//            steps{
//                echo "provisioning EKS Cluster."
//                script{
//                    dir('terraform'){
//                        sh "terraform init"
//                        sh "terraform apply --auto-approve"
//                    }
//                }
//            }
//        }
        stage("check deployment"){
            steps{
                script {
                    sh "aws eks update-kubeconfig --name eks_cluster --region eu-central-1"
                    sh "kubectl get node"
                }
            }
        }
        stage("install argo cd"){
            steps{
                script {
                    sh "kubectl create namespace argocd"
                    sh "kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.4.7/manifests/install.yaml"
//                    sh "curl --silent --location -o /usr/local/bin/argocd https://github.com/argoproj/argo-cd/releases/download/v2.4.7/argocd-linux-amd64"
//                    sh "chmod +x /usr/local/bin/argocd"
                }
            }
        }
//        stage("deploy") {
//            environment{
//                DOCKER_HUB_CREDITS = credentials("dockerHubCredit") //now DOCKER_HUB_CREDITS_USR and DOCKER_HUB_CREDITS_PSW will have user and pass.
//            }
//            steps {
//                script {
//                    echo "waiting for the aws instance to complete initializing."
//                    sleep(time: 60, unit: "SECONDS")
//                    echo "deploying the application..."
//                    echo "IP : ${SERVER_IP}"
//                    def shellCommand = "bash ./shell-cmd.sh ${IMAGE_NAME}:${IMAGE_VERSION} ${DOCKER_HUB_CREDITS_USR} ${DOCKER_HUB_CREDITS_PSW}"
//                    def ec2Instance = "ubuntu@${SERVER_IP}"
//                    sshagent(["aws_ssh_key"]) {
//                        sh "scp -o StrictHostKeyChecking=no shell-cmd.sh ${ec2Instance}:/home/ubuntu"
//                        sh "scp -o StrictHostKeyChecking=no docker-compose.yaml ${ec2Instance}:/home/ubuntu"
//                        sh "ssh -o StrictHostKeyChecking=no ${ec2Instance} ${shellCommand}"
//
//                    }
//                }
//            }
//        }
//
//
    }
}