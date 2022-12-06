pipeline{
    agent:{
        docker { 
            image "node:18-alpine3.15" 
        }
    }

    stages{
        stage("clone"){
            steps{
                sh:'git clone https://github.com/pauloCastillo/DevOps-Final_usip.git'
            }
        }
        stage("build"){
            steps{
                sh:"node --version"
                sh:'npm install'
            }
        }

        // stage("test"){}
        stage("package"){}
        stage("deploy"){
             sh:'npm run build'
        }
    }
}