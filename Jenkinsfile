pipeline {
    agent {
        label 'base'
    }
    options {
        disableConcurrentBuilds()
        timestamps()
    }
    stages {
        stage('Build and Release') {
            when {
                branch 'master'
            }
            steps {
                container ('base') {
                    sh 'docker build . -t $DOCKER_REGISTRY/fluentd-es-aws:latest'
                    sh 'aws ecr get-login --no-include-email --region eu-west-1 | sh'
                    sh 'docker push $DOCKER_REGISTRY/fluentd-es-aws:latest'
                }
            }
        }
    }
}
