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

post {
    success {
        echo 'Build success through GitHub webhook'

        publishChecks(
            name: 'Jenkins-CI-Status',
            title: 'Amazon Jenkins CI Build',
            summary: 'Maven CI pipeline execution',
            text: 'Checkout, Compile, Test and Build completed'
        )
    }

    failure {
        echo 'Failure in the build'

        publishChecks(
            name: 'Jenkins-CI-Status',
            title: 'Amazon Jenkins CI Build',
            summary: 'Maven CI pipeline failed',
            text: 'Please check Jenkins Console Output'
        )
    }
}


}
