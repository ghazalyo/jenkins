pipeline {
  agent {label 'agents'}
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
        archiveArtifacts(artifacts: '**/*.war', onlyIfSuccessful: true)
      }
    }

    stage('DEPLOY') {
      steps {
        sh "echo deploy"
deploy adapters: [tomcat9(credentialsId: '11c1faf2-b487-4249-aaaf-afca030eaee5', path: '', url: '172.17.0.5:8080')], contextPath: '/chocolat', war: 'target/*.war'
    }

  }
}
}
