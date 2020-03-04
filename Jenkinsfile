pipeline {
  agent any
  stages {
    stage('Do some stuff') {
      when {
        branch 'qa'
          }
      options {
         enforceBuildSchedule()
              }
      steps {
        echo 'this can wait til morning'
        echo 'yes'
      }
    }
  }
}
