node {
    def app
    stage('Clone repository') {
        checkout scm
    }

    stage('Build image') {
        app = docker.build("danielsaska/datlas","-f ./Dockerfile .")
    }

    stage('Push image') {
        docker.withRegistry('https://docker.io', 'docker-hub-credentials') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}
