pipeline {
  node (jenkins-jenkins-slave){
    options {
      timeout(time: 5, unit: 'MINUTES')
      disableConcurrentBuilds()
      buildDiscarder(logRotator(numToKeepStr: '10'))
    }
    stages {
      stage('Config Context') {
        steps {
          container('jenkins-slave'){
            script{
              sh "kubectl -n development run nginx --image=nginx"
            }
          }
        }
      }
    }
  }
}
