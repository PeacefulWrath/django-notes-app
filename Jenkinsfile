@Library('Shared')_
pipeline {
    agent { label "vinod"}
    stages{
        stage("Hello"){
            steps {
                script{
                    hello()
                }
            }
        }
        stage("Clone Code"){
            steps{
                script{
                     clone("https://github.com/PeacefulWrath/django-notes-app.git","dev")
                }
            }
        }
        stage("Build and Test"){
            steps{
                script{
                    docker_build("notes-app","latest","devopsexpertsrinja")
                }
                // sh "docker build . -t notes-app"
            }
        }
        stage("Push to Docker Hub User devopsexpertsrinja"){
            steps{
                // withCredentials([usernamePassword(credentialsId:"dockerHubCred",passwordVariable:"dockerHubPass",usernameVariable:"dockerHubUser")]){
                // sh "docker tag notes-app ${env.dockerHubUser}/notes-app:latest"
                // sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                // sh "docker push ${env.dockerHubUser}/notes-app:latest"
                // }
                
                script{
                    docker_push("notes-app","latest","devopsexpertsrinja")
                }
            }
        }
        stage("Deploy"){
            steps{
                // sh "docker compose down && docker compose up -d"
                script{
                    docker_compose()
                }
            }
        }
    }
}
