pipeline {
    agent { node {label 'ubuntu'} }
      stages {
        stage('vcs') {
            steps{
                git branch: 'main',
                url: 'https://github.com/Kiranteja623/jenkins-k8s-deploy.git'
            }
            
        }
        stage('build image') {
            steps {
                sh 'cd ${Workspace} && docker image build -t nopcommerce:28.0 .'
                sh 'docker tag nopcommerce:28.0 kiranteja623/nopcommerce:28.0'
                sh 'docker push kiranteja623/nopcommerce:28.0'
            }
        }
        stage('deploying application') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
                sh 'kubectl get po'
                sh 'kubectl get svc'
            }
        }
    }
}
