#!groovy


@Library("jenkinsSharedLib")
def gv
pipeline {
    agent any
    stages{
        stage("initial stage"){
            steps {
                echo "this is only test"
            }
        }
    }
//    tools {
//        maven 'Maven'
//    }
//
//    environment {
//        IMAGE_NAME = "grahamtty/netflix"
//        IMAGE_VERSION = "latest"
//        AWS_ACCESS_KEY_ID = credentials('aws_access_key_id') //this is like exporting params. so it is enough to automatically login aws.
//        AWS_SECRET_ACCESS_KEY = credentials("aws_secret_access_key")
//    }
//    stages {
//
//        stage("build jar") {
//            steps {
//                echo "building the application..."
//                sh 'mvn clean package'
//            }
//        }
//
//        stage("build image") {
//            steps {
//                echo "building docker image..."
//                script {
//                    buildDockerImage("$env.IMAGE_NAME:$env.IMAGE_VERSION")
//                    loginDocker("dockerHubCredit")
//                    pushDockerImage("$env.IMAGE_NAME:$env.IMAGE_VERSION")
//                }
//            }
//        }
//
//        stage("provision server"){
//            environment{
//                AWS_ACCESS_KEY_ID = credentials('aws_access_key_id') //this is like exporting params. so it is enough to automatically login aws.
//                AWS_SECRET_ACCESS_KEY = credentials("aws_secret_access_key")
////                    TF_VAR_env_prefix = 'test' #the way to change a terraform var inside jenkins file.
//            }
//            steps{
//                echo "provisioning aws server(s)."
//                script{
//                    dir('terraform'){
//                        sh "terraform init"
//                        sh "terraform apply -var-file terraformVars.tfvars --auto-approve"
//                        SERVER_IP = sh(
//                                script: "terraform output myapp_server_ip",
//                                returnStdout: true
//                        ).trim()
//                    }
//                }
//            }
//        }
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
//    }
}