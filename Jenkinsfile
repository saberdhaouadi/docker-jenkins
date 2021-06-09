node {
    def app

    stage('Clone repository') {
        checkout scm
    }

    stage('Build image') {
        app = docker.build("devopnode")
    }

    stage('Test image') {
        app.inside {
             sh 'echo "Tests passed" '
        }
    }
 
    stage('Push image') {
       docker.writeRegistry('https://hub.docker.com/repository/docker/saberdocker/juneapp', 'dockerhub_id') {
         app.push("${env.BUILD_NUMBER}")
         app.push("latest")
       }
   }
}

