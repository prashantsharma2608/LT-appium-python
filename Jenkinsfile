pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout([$class: 'GitSCM',
                  branches: [[name: '*/main']],
                  userRemoteConfigs: [[url: 'https://github.com/prashantsharma2608/LT-appium-python.git']]])
      }
    }

    stage(D){
      steps{
        bat 'wget https://path-to-lt-binary/lambdatest-tunnel.zip'
        bat 'unzip lambdatest-tunnel.zip'
      }
    }

    stage(S){
      steps{
        bat './lambdatest-tunnel --user prashantsharma --key RlEUtZdSXJkl3iEtXNx6eWFSyLBfDJlkYRYG1igfb1OjpXfXRp'
      }
    }

    stage('Test') {
      steps {
        bat 'pip install -r requirements.txt'
        // bat 'python -m pip install pytest'
        bat 'python android.py'
      }
    }

    stage('kill_tunnel'){
      steps{
        bat './lambdatest-tunnel --user YOUR_USERNAME --key YOUR_ACCESS_KEY --kill'
      }
    }
    
    stage('Report'){
      steps{
        lambdaTestReportPublisher 'automation'
      }
    }
  }
}
