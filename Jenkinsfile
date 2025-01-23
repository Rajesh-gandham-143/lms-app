pipeline{
    agent any
    stages{
        stage('deploy_webapp') {
            steps{
                sh 'cd webapp'
                sh 'ls'
                sh 'docker build -t rajesh_node .'
                sh 'docker run -dt --name lms_webapp -p 90:80 rajesh_node'
            }
        }
    }
}