pipeline {
    agent any
    tools {
        'org.jenkinsci.plugins.docker.commons.tools.DockerTool' 'Docker_tools'
    }
    stages {
        stage('Verify GIT Branch') {
            steps {
                echo "Current branch: ${env.GIT_BRANCH}"
            }
        }
        stage('Docker Build') {
            steps {
                script {
                    docker.image('docker:20.10.6').inside('--privileged -v /var/run/docker.sock:/var/run/docker.sock:z') {
                        sh 'docker --version'
                        sh 'docker compose -f docker-compose.yml build'
                    }
                }
            }
        }
    }
}
