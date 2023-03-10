pipeline {
    agent{
        node {
            label "nodeslave"
        }
    }
    tools {nodejs "node-js"}
    stages{
        stage ("clone the code"){
            steps{
                git branch: 'main', url: 'https://github.com/Bathalapalli-SaiRangaPavan/NodeJs-Project1-CI-CD.git'
            }
        }
       
        stage ("Build the code"){
            steps{
                sh "npm install"
            }
        }

        stage ("Unit test"){
            steps{
                sh "npm test"
            }
        }
    }
}
