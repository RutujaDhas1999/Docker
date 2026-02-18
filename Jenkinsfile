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
                docker cp index.html Q2:/usr/local/apache2/htdocs/

                '''
            }
        }
    }

    stage('Deploy Q2') {
        agent { label 'slave2' }

        steps {
            dir('q2') {
                git branch: '2026Q2', url: 'https://github.com/RutujaDhas1999/Docker.git'

                sh '''
                docker rm -f Q2 || true
                docker run -d -p 8081:80 --name Q2 httpd
                docker cp index.html Q2:/usr/local/apache2/htdocs/
                '''
            }
        }
    }

}


}
