groovy
    // Jenkinsfile
    pipeline {
        agent any
        stages {
            stage('Build') {
                steps {
                    script {
                        dockerImage = docker.build("your-dockerhub-username/hello-world-app")
                    }
                }
            }
            stage('Push') {
                steps {
                    script {
                        docker.withRegistry('https://index.docker.io/v1/', 'docker-hub-credentials') {
                            dockerImage.push("latest")
                        }
                    }
                }
            }
            stage('Deploy') {
                steps {
                    sh 'docker run -d -p 5000:5000 your-dockerhub-username/hello-world-app:latest'
                }
            }
        }
    }