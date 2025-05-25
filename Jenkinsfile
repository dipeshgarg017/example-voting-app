pipeline{
    agent{label 'worker'}
    options { 
        buildDiscarder(logRotator(numToKeepStr: '15'))
        disableConcurrentBuilds()
        retry(2)
        timeout(time: 10, unit: 'MINUTES')
    }
    stages{
        stage("Docker build and push"){
            steps{
                sh "docker login -u dipesh017 -p Arvi.1418"
                sh '''
                    cdWQ vote
                    docker build -t dipesh017/vote:v${BUILD_NUMBER} .
                    '''
                sh "docker push dipesh017/vote:v${BUILD_NUMBER}"
            }
        }
        stage("Deploy"){
            steps{
                sh "echo docker deploy"
            }
        }
    }
}
