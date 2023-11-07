pipeline {
    agent any

    environment {
        JENKINS_JOB_NAME = "${env.JOB_NAME}"
        JENKINS_WORKSPACE = "${WORKSPACE}"
    }

    stages {
        stage("Pull BACKEND image from Docker-hub") {
            steps {
                sh "echo JOBNAME: ${JENKINS_JOB_NAME}"
                sh "echo WORKSPACE: ${JENKINS_WORKSPACE}"
                sh "docker pull rhuayhua/jpas-backend"
            }
        }

        stage("Pull UI image from Docker-hub") {
            steps {
                sh "echo JOBNAME: ${JENKINS_JOB_NAME}"
                sh "echo WORKSPACE: ${JENKINS_WORKSPACE}"
                sh "docker pull rhuayhua/jpas-frontend"
            }
        }

        stage("START JPAS APP") {
            steps {
                sh "docker-compose up -d"
            }
        }
    }

    post {
        always {
            sh "echo DONE!!"
        }
    }

}