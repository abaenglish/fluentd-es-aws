node {
    def fd

    stage('build') {
        checkout scm
        fd = docker.build("abaenglish/fluentd-es-aws")
    }

    stage('push') {
        docker.withRegistry('http://nexus.aba.land:5000', 'nexus-user') {
            fd.push("${env.BUILD_NUMBER}")
            fd.push("latest")
        }
    }
}
