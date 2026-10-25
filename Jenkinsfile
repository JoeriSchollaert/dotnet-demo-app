node {
    stage('Preparation') {
        catchError(buildResult: 'SUCCESS') {
            sh 'docker-compose down'
        }
    }
    stage('Checkout') {
        checkout scm
    }
    stage('Build and Deploy') {
        sh 'cd /var/jenkins_home/workspace/DotnetDemoApp && docker-compose up -d --build'
    }
    stage('Initialise database') {
        sh 'cd /var/jenkins_home/workspace/DotnetDemoApp && docker exec -i todoappdb mariadb -utodo_usr -pletmeinplz todo_db < TodoApp/schema.sql'
    }
}