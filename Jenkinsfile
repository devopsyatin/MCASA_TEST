pipeline {
    agent any 
        options {
        enforceBuildSchedule(branches: ['master', 'qa'])
                  }
  stages {
    stage('Do some stuff') {
      steps {
        echo 'this can wait til morning'
        echo 'yes'
      }
    }
  }
}
