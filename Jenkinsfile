node('appserver_3120_60') {
    def app

    stage('Cloning Git') {
        checkout scm
    }

    stage('Build and Tag') {
        app = docker.build('abe6191990/snakegame1')
    }

    stage('SAST SNYK') {
        echo "Running security analysis with SNYK"
        // Add SNYK commands here if required
    }

    stage('Post to DockerHub') {
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_credentials') {
            app.push('latest')
        }
    }

    stage('Deploy') {
        sh "docker-compose down"
        sh "docker-compose up -d"
    }
}
