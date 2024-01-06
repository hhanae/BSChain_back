node {
    def dockerImageTag = "hanae/bschain${env.BUILD_NUMBER}"
    def networkName = "mynetwork"
    def buildNumber = env.BUILD_NUMBER
    def minikubeProfile = "minikube"

    try {
        stage('Clone Repo') {
            git url: 'https://github.com/hhanae/BSChain_back.git',
            branch: 'master'
        }

        stage('Docker Login') { 
            sh "docker login -u hanae.hanim01@gmail.com -p dckr_pat_vtjWPfET53gWCiICfk6G2mMKPUI"
        }

        stage('Build Docker Images') {
            docker.build("hanae/bschain:${buildNumber}")
          
        }

        stage('Push Docker Images to Docker Hub') {
            echo "Pushing Docker images to Docker Hub"
            docker.image("hanae/bschain:${buildNumber}").push()
        }

    } catch (Exception e) {
        throw e
    }
}

