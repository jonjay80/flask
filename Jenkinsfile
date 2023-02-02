pipeline {
    environment {
        registry = 'jonjay80/flask_app'
        registryCredentials = 'docker'
        cluster_name = 'skillstorm'
    }
  agent {
    node {
      label 'docker'
    }

  }
  stages {
    stage('Git') {
      steps {
        git(url: 'https://github.com/jonjay80/flasking', branch: 'main')
      }
    }
stage('Build Stage') {
    steps {
        script {
            dockerImage = docker.build(registry)
        }
    }
}
stage('Deploy') {
    steps {
        script {
            docker.withRegistry('', registryCredentials) {
                dockerImage.push()
            }
        }
    }
}
}
}