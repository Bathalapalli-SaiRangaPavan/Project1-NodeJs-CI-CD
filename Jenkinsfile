def registry = "https://bsairangapavan.jfrog.io/"
def imageName = "bsairangapavan.jfrog.io/nodebuild-docker/newimageversion" 
def version   = "1.0.0"
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
        stage(" Docker Build ") {
            steps {
                script {
                    app = docker.build(imageName+":"+version)
                }
            }
        }
        stage (" Docker Publish "){
            steps {
                script { 
                   docker.withRegistry(registry, 'Jfrog-token'){
                      app.push()
                    }    
                }
            }
        }  
    }
}
