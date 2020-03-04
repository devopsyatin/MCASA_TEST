pipeline {
    agent {
        node {
            label 'midtier-slave'
          properties([enforceBuildSchedule(branches: ['qa', 'master')])
        }
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
