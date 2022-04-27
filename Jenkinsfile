pipeline{
    agent any
    stages {
        stage('SCM Checkout') {
            steps{
                git url: 'https://github.com/AkashBG3010/NodeJs-API.git', branch: 'master'
            }
        }
        stage('Deploy App on k8s') {
            steps {
                sshagent(['kops-machine']) {
                    sh "scp -o StrictHostKeyChecking=no nodejs-app.yml ubuntu@3.239.164.243:/home/ubuntu"
                    script {
                        try{
                            sh "ssh ubuntu@3.239.164.243 kubectl create -f nodejs-app.yml"
                        }
                        catch(error){
                            sh "ssh ubuntu@3.239.164.243 kubectl create -f nodejs-app.yml"
                        }
                    }
                }
            }
        }
    }
}
