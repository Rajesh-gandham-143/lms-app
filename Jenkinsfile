pipeline{
    agent any
    stages{
        stage('deploy_webapp') {
            steps{
                script {
                sh '''
                cd webapp
                ls
                docker build -t rajesh_node .
                docker run -dt --name lms_webapp -p 90:80 rajesh_node
                '''
                }
            }
        }
    }
}