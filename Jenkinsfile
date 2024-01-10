pipeline {
    environment {
        imagename = "aredan/ansible-ee-mikrotik"
        registryCredential = 'dockerhub_id'
        dockerImage = ''
    }
    agent any
    stages {

        stage('Cloning Git') {
        steps {
            git([url: 'https://github.com/aaNetworks/ansible-ee-mikrotik.git', branch: 'main'])

        }
        }

        stage("Build EE") {
            steps {
                echo "Building Ansible Execution Environment"
                sh "/home/ariel/.local/bin/ansible-builder build --tag ansible-ee-mikrotik --container-runtime docker"
            }
        }

        stage('Remove Unused docker image') {
            steps
            {
            // sh "docker rmi $imagename:$BUILD_TIMESTAMP"
            // sh "docker rmi $imagename:latest"
            sh "docker system prune -af --volumes"

            }
        }
    }
}