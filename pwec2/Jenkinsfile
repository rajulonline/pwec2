pipeline {
  agent {
    dockerfile {
      customWorkspace '/pwec2'
      filename 'Dockerfile'
    }
  }
  stages {
    stage('Test') {
      steps {
        sh '''
          node --version
          git --version
          curl --version
        '''
      }
    }
  }
}
