pipeline {
    agent any

    environment {
        IMAGE_NAME = "praveen2205/2023bcs0115"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/praveen-2205/myapp-cicd.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ${IMAGE_NAME} .'
            }
        }

        stage('Login to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds',
                    usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                sh 'docker push ${IMAGE_NAME}'
            }
        }
    }
}
```

> ✏️ Replace `YOUR_GITHUB_USERNAME` with your actual GitHub username

---

## Where to Save It

Your folder structure should look like this:
```
myapp/
├── index.html
├── Dockerfile
└── Jenkinsfile        ← save here (no .txt, no extension)