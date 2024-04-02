stage('Validate Docker-Compose') {
    steps {
        script {
            sh 'docker run --rm -v /var/run/docker.sock:/var/run/docker.sock -v "${PWD}":/work -w /work docker/compose:1.29.2 config --no-interpolate'
        }
    }
}
