node {
    stage("scm") {
        git url: 'https://github.com/dralluy/picalculator'
    }
    stage("test and build") {
        sh "docker build -t dralluy/picalculator ."
    }
    stage("push") {
        withCredentials([[
            $class: 'UsernamePasswordMultiBinding', 
             credentialsId: 'docker_hub',
             usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD'
        ]]) {
            sh "docker login -u $USERNAME -p $PASSWORD"
            sh "docker push dralluy/picalculator"
        }
    }
}
