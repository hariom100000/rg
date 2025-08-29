pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            echo 'Jenkins Minute pipeline'
          }
        }

        stage('terraform-init') {
          steps {
            sh '''terraform init
terraform plan'''
          }
        }

      }
    }

  }
}