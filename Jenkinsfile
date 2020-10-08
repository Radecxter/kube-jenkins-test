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

    stages {
        stage('Config Context') {
            steps {
                container('jenkins-slave'){
		    sh "echo 'reached'"
                    sh "kubectl -n development run nginx --image=nginx"
                }
            }
        }
    }
}

