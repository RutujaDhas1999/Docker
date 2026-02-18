pipeline {
agent none

    triggers {
        githubPush()
    }
stages {

    stage('Deploy Q1') {
        agent { label 'slave1' }

        steps {
            dir('q1') {
                git branch: '2026Q1', url: 'https://github.com/RutujaDhas1999/Docker.git'

                sh '''
                docker rm -f Q1 || true
                docker run -d -p 80:80 --name Q1 httpd
                docker cp index.html Q1:/usr/local/apache2/htdocs/

                '''
            }
        }
    }



}


}
