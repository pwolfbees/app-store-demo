pipeline {
  agent {
    node {
      label 'java'
    }
    
  }
  stages {
    stage('Build T1000') {
      steps {
        sh 'mvn clean source:jar package'
        sleep 10
      }
    }
    stage('Validate Systems') {
      parallel {
        stage('Visual') {
          steps {
            sh 'echo \'setting up selenium environment\''
          }
        }
        stage('Weapons') {
          steps {
            sh 'echo \'setting up selenium environment\''
          }
        }
        stage('Recovery') {
          steps {
            sh 'echo \'setting up selenium environment\''
          }
        }
      }
    }
    stage('Battle Testing') {
      steps {
        sh 'mvn findbugs:findbugs'
        sleep 60
      }
    }
    stage('Deploy') {
      parallel {
        stage('Deploy') {
          steps {
            sh 'mvn source:jar package -Dmaven.test.skip'
          }
        }
        stage('Time Travel') {
          steps {
            echo 'sss'
          }
        }
      }
    }
    stage('Skynet') {
      parallel {
        stage('Blow stuff up') {
          steps {
            echo 'Just kidding lol'
            sleep 25
          }
        }
        stage('Locate John Connor') {
          steps {
            sleep 43
          }
        }
      }
    }
    stage('I\'ll be back') {
      steps {
        sleep 10
      }
    }
  }
  post {
    always {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive '**/target/*.jar'
      
    }
    
  }
}