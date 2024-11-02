node('appserver_3120_60')
{
    def app
    {
     stage('cloning Git') 
     checkout scm  
    }
    stage('Build-and-Tag')
    {
    app = docker.build('abe6191990/snakegame1')
    }
    stage(SAST-SNYK)
    {
    echo "test"
    }
    stage('Post-to-dockerhub')
    {
        docker.withregistry('https://registry.hub.docker.com', 'dockerhub_credentials')
        {
            app.push('latest')
        }
    }
    stage('Deploy')
    {
        sh "docker-compose down"
        sh "docker-compose up -d"
    }
}
