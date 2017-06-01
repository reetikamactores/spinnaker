node {
    def app

    stage('Clone repository') {
        checkout scm
    }

    stage('Build image') {
        app = docker.build("reetikarepo.mactores.com/spinnaker")
    }


    stage('Test image') {
        app.inside {
            sh 'echo "Tests passed"'
        }
    }


    stage('Push image') {
        docker.withRegistry('https://reetikarepo.mactores.com', 'docker-hub-credentials') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }

}
