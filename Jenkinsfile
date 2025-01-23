pipeline{
    agent any
    stages{
        stage('deploy_webapp') {
            steps{
                sh 'docker run -d --name lms_database -p 5432:5432 -e POSTGRES_PASSWORD=datauser --network lms_net postgres'
            }
        }
        stage('deploy_api') {
            steps{
                script {
                    sh '''
                    cd api
                    docker build -t rajesh_api .
                    docker run -d --name lms_api -p 3000:3000 --network lms_net rajesh_api
                    '''
                }
            }
        }
        stage('deploy database'){
            steps{
                script {
                sh '''
                rm -rf /usr/local/apache2/htdocs/*
                cd webapp
                ls
                docker build -t rajesh_node .
                docker run -dt --name lms_webapp -p --network lms_net 90:80 rajesh_node
                '''
                }
            }
        }
    }
}