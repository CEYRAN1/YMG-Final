pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                checkout scmGit(
                    branches: [[name: '*/master']],
                    userRemoteConfigs: [[url: 'https://github.com/CEYRAN1/YMG-Final']]//projenin urlsi
                )
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    docker.build("ders:${env.BUILD_NUMBER}")
                }
            }
        }
        stage('Push image to Hub'){
            steps{
                script{
                    docker.image("ders:${env.BUILD_NUMBER}").run("-d -p 8080:80 --name demo")
                }
            }
  }
}

}