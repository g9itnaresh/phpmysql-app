node{

    stage('SCM Checkout')
    {
        git credentialsId: '5ce9b303-9871-41cf-ad4a-ffb3083abfd3', url: 'https://github.com/g9itnaresh/phpmysql-app.git'
    }
    
    stage('Run Docker Compose File')
    {
        sh 'docker-compose build'
        sh 'docker-compose up -d'
    }
    stage('PUSH image to Docker Hub')
    {
        withCredentials([string(credentialsId: 'DockerHubPassword', variable: 'DHPWD')]) 
        {
            sh "docker login -u vardhanns -p ${DHPWD}"
        }
        sh 'docker push vardhanns/phpmysql_app'
    }
}
