pipeline {
  agent {
    node {
      label 'java'
    }
    
  }
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean source:jar package'
        sleep 10
      }
    }
    stage('Browser Tests') {
      parallel {
        stage('Firefox') {
          steps {
            sh 'echo \'setting up selenium environment\''
          }
        }
        stage('Safari') {
          steps {
            sh 'echo \'setting up selenium environment\''
          }
        }
        stage('Chrome') {
          steps {
            sh 'echo \'setting up selenium environment\''
          }
        }
      }
    }
    stage('Static Analysis') {
      steps {
        sh 'mvn findbugs:findbugs'
      }
    }
    stage('Deploy') {
      steps {
        sh 'mvn source:jar package -Dmaven.test.skip'
      }
    }
    stage('Train Skynet') {
      steps {
        echo 'Just kidding lol'
        sleep 25
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