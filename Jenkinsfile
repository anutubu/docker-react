pipeline {
    environment {
    registry = "anyoneb/docker_automation"
    registryCredential = 'dockerhub'
    dockerImage = ''
    }

    agent any
    stages {
            stage('Cloning our Git') {
                steps {
                    git url: 'https://github.com/anutubu/docker-react.git',
                        credentialsId: 'github'
                    }
                }

            stage('Building Docker Image') {
                steps {
                    sh "docker build -t anyoneb/docker-react -f Dockerfile.dev ."
                }
            }

            stage('Running Docker image and test suites') {
                steps {
                    sh 'docker run -e CI=true anyoneb/docker-react npm run test -- --coverage'
                }
            }
            

        }
    }
