
pipeline {
    agent any 
    stages {
        stage('CloningRepo') { 
            steps {
			    sh 'sudo rm -fr /var/lib/jenkins/workspace/my-app'
				sh 'git -C /var/lib/jenkins/workspace clone https://github.com/indraindrajit71/my-app.git'
				sh 'sudo cp -pr /var/lib/jenkins/workspace/  /var/lib/jenkins/jobs/devopspipeline/workspace'
				sh 'mvn clean -f /var/lib/jenkins/jobs/devopspipeline/workspace/my-app'
            }
        }
        stage('Test') { 
            steps {
                sh 'mvn test -f /var/lib/jenkins/jobs/devopspipeline/workspace/my-app'
            }
        }
        stage('Deploy') { 
            steps {
                sh 'mvn package -f /var/lib/jenkins/jobs/devopspipeline/workspace/my-app'
            }
        }
    }
}
