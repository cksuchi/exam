pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean install'  // Example: Maven build
      }
    }
    stage('Test') {
      steps {
        sh 'mvn test'  // Example: Maven tests
        junit '**/target/surefire-reports/*.xml'
      }
    }
    stage('Deploy') {
      steps {
        sh 'echo "Deploying..."'  // Replace with actual deployment commands
      }
    }
  }
}
        if: github.ref == 'refs/heads/main' # Deploy only on main branch
        run: echo "Deploying to production" # Replace with your actual deployment command
