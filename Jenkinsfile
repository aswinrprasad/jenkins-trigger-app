pipeline {
    agent any

    stages{
        steps('Git Checkout'){
            checkout scm
        }
        steps('Docker Image Build & Push')
            docker.withRegistry('https://registry.hub.docker.com', 'dockeHub') {

            def customImage = docker.build("aswinrprasad/jenkins-trigger-web:${env.BUILD_ID}")

            /* Push the container to the custom Registry */
            customImage.push()
        }
        steps('Complete'){
            sh "echo 'Build Successful'"
        }
    }
}