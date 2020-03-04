pipeline {
    agent {
        properties([enforceBuildSchedule(branches: ['qa', 'master'])])
        node {
            label 'midtier-slave'
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
