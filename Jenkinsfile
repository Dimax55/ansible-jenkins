#!groovy
//  groovy Jenkinsfile
properties([disableConcurrentBuilds()])\

pipeline  {
        agent { 
           label ''
        }

    options {
        buildDiscarder(logRotator(numToKeepStr: '10', artifactNumToKeepStr: '10'))
        timestamps()
    }
    stages {
        stage("Git clone") {
            steps {
                sh '''
                cd /var/lib/jenkins/workspace/
                rm -rf ansible-jenkins
                git clone https://github.com/Dimax55/ansible-jenkins.git
                '''
            }                
        }    
        stage("Build") {
            steps {
                sh '''
                cd /var/lib/jenkins/workspace/ansible-jenkins/Ansinle
                docker build -t dimax555/ansivle .

                '''
            }
        } 
        stage("docker run") {
            steps {
                sh '''
                docker run \
                --name ansible \
                -d dimax555/ansivle

                '''
            }
        }
        

      
    }
}
