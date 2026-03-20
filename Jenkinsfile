pipeline {
agent any

```
environment {
    DOCKERHUB_USERNAME = 'sunoj9249'
    IMAGE_FRONTEND = "${DOCKERHUB_USERNAME}/reg_roll_frontend"
    IMAGE_BACKEND  = "${DOCKERHUB_USERNAME}/reg_roll_backend"
}

stages {

    stage('Checkout') {
        steps {
            git 'https://github.com/your-repo.git'
        }
    }

    stage('Build Images') {
        steps {
            sh 'docker build -t $IMAGE_FRONTEND ./frontend'
            sh 'docker build -t $IMAGE_BACKEND ./backend'
        }
    }

    stage('Push Images') {
        steps {
            withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                sh 'echo $PASS | docker login -u $USER --password-stdin'
                sh 'docker push $IMAGE_FRONTEND'
                sh 'docker push $IMAGE_BACKEND'
            }
        }
    }
}
```

}
