pipeline{
    agent{label 'worker'}
    options { 
        buildDiscarder(logRotator(numToKeepStr: '15'))
        disableConcurrentBuilds()
        retry(2)
        timeout(time: 10, unit: 'MINUTES')
    }
    parameters {
        string(name: 'BRNACH', defaultValue: 'develop', description: '')
        booleanParam(name: 'TEST_CASES', defaultValue: true, description: '')
        choice(name: 'ENV', choices: ['dev', 'qa', 'uat'], description: '')
    }
    stages{
        stage("Docker build and push"){
            steps{
                sh "docker login -u dipesh017 -p Arvi.1418"
                sh '''
                    cd vote
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
