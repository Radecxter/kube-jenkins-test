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
                  withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'svc_alm', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
                    script{              
			  sh "echo 'reached'"
                          sh "kubectl -n default run nginx --image=nginx"
                    }
                  }
                }
            }
        }
    }
}

