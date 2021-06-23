pipeline {
    agent {
        label 'docker'
    }
    stages {
        stage('build') {
            steps {
                script {
                    docker.withRegistry('https://registry.cuberite.org', 'e01ba3f6-30a8-4475-af70-92305efe526f') {
                        docker.build('cuberite/docker-ci/android:latest', 'android').push()
                        docker.build('cuberite/docker-ci/minimal:latest', 'minimal').push()
                        docker.build('cuberite/docker-ci/armhf:latest', 'armhf').push()
                        docker.build('cuberite/docker-ci/users-manual:latest', 'users-manual').push()
                    }
                }
            }
        }
    }
}
