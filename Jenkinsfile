node {
    def dockerImage

    stage('Clone repository') {
        git branch: 'main', 
            credentialsId: 'github-access', 
            url: 'https://github.com/kjcho805/rolling-paper.git'
    }
    
    stage('Build image') {
        dir('docker-project-front') {
            dockerImage = docker.build("aws7th/node-front:1.0")
        }
    }
    
    stage('Push image') {
        withDockerRegistry([ credentialsId: "docker-access", url: "" ]) {
            dockerImage.push()
        }
    }
}

