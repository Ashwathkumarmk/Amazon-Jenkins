pipeline {
    agent any
    stages {

        stage('pull scm git ') {
            steps {
                git branch: 'main', url: 'https://github.com/Ashwathkumarmk/Amazon-Jenkins.git'
            }
        }
        stage('compile ') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('build') {
            steps {
                 sh 'mvn clean install'
            }
        }

        
    }

  post{

  success{
     echo 'Build success through GitHub webhook'
  }
    
  failure{
       echo 'Failure in the build'
   }

  }


}
