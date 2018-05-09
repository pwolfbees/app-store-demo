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
        stage('Internet Explorer') {
          steps {
            sh 'echo \'setting up selenium environment\''
            sleep 5
          }
        }
      }
    }
    stage('Static Analysis') {
      steps {
        sh 'mvn findbugs:findbugs'
      }
    }
    stage('Deploy to QA') {
      steps {
        sh 'mvn source:jar package -Dmaven.test.skip'
      }
    }
    stage('Manual QA') {
      parallel {
        stage('UAT') {
          steps {
            input(message: 'Are you sure this is a good thing?', ok: 'Great')
          }
        }
        stage('Performance') {
          steps {
            sh 'printenv'
            input(message: 'Por que no lo dos?', ok: 'Si')
          }
        }
      }
    }
    stage('Deploy to Production') {
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