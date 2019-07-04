pipeline {
    agent { docker { image 'maven:3.3.3' } }

    environment {
      DB_ENGINE = 'sqlite'
    }

    stages {
        stage('build') {
            steps {
              retry(3) {
                sh 'mvn --version'
              }
              timeout(time: 3, unit: 'MINUTES') {
                sh 'echo " Hello World"'
              }
              sh 'printenv'
              sh '''
                echo "Multiline shell steps works too"
                ls -lah
              '''
            }
        }
    }

    post {
      always {
        echo 'This pipeline finsihed'
      }
      success {
        echo 'This pipeline runs successfully'
      }
      failure {
        echo 'Pipeline Failed'
      }
      unstable {
        echo 'This will run only if the run was marked as unstable'
      }
      changed {
        echo 'State of Pipeline changed'
      }
    }
}
