node {
    def fd

    stage('build') {
        fd = docker.build("abaenglish/fluentd-es-aws")
    }

    stage('push') {
        docker.withRegistry('http://nexus.aba.land:5000', 'nexus-credentials') {
            fd.push("${env.BUILD_NUMBER}")
            fd.push("latest")
        }
    }
}
