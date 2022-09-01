pipeline {
  agent any
  stages {
    stage('BUILD') {
      steps {
        sh 'mvn clean install'
      }
    }

    stage('TEST') {
      steps {
        sh 'echo Test'
      }
    }

    stage('POST BUILD') {
      steps {
        archiveArtifacts(artifacts: '*/*.war', onlyIfSuccessful: true)
      }
    }

    stage('DEPLOY') {
      steps {
        #sh 'rm -r /home/jenkins/webapps/spark.war'
        sh 'cp target/*.war /home/jenkins/webapps/spark.war'
      }
    }

  }
}
