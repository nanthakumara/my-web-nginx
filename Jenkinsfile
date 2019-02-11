node{
   stage('SCM Checkout'){
       git credentialsId: 'git-cred', url: 'https://github.com/nanthakumara/my-web-nginx'
   }
   stage('Build Docker Image'){
     sh 'docker build -t nanthakumara/my-nginx1-app:3.0.0 .'
   }
   stage('Push Docker Image'){
     withCredentials([string(credentialsId: 'docker-pwdd', variable: 'dockerhubpwd')]) {
        sh "docker login -u nanthakumara -p ${dockerHubPwd}"
     }
     sh 'docker push nanthakumara/my-nginx1-app:3.0.0'
   }
   stage('Run Container on Dev Server'){
     def dockerRun = 'docker run -p 80:80 -d --name my-nginx1-app nanthakumara/my-nginx1-app:3.0.0'
     sshagent(['dev-server']) {
       sh "ssh -o StrictHostKeyChecking=no ec2-user@172.31.85.5 ${dockerRun}"
     }
   }
}
