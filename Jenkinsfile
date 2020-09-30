pipeline {
    agent {
        kubernetes {
            yamlFile 'jenkins-slave.yaml'
        }
    }

  options {
    timeout(time: 5, unit: 'MINUTES')
    disableConcurrentBuilds()
    buildDiscarder(logRotator(numToKeepStr: '10'))
  }

  environment {
    NAMESPACE = 'development'
  }

    stages {
        stage('Config Context') {
            steps {
                container('jenkins-slave'){
                    script{
                        sh "kubectl -n ${NAMESPACE} run nginx --image=nginx"
                    }
                }
            }
        }
    }
}
