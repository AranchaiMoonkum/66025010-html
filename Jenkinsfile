pipeline {
    agent any
    stages {      
        stage("Copy file to Docker server"){
            steps {
                sh "scp -r /var/lib/jenkins/workspace/66025010-nextjs/* root@43.208.253.87:~/66025010-nextjs"
            }
        }
        
        stage("Build Docker Image") {
            steps {
				ansiblePlaybook playbook: '/var/lib/jenkins/workspace/66025010-nextjs/playbooks/build.yaml'
            }    
        } 
        
        stage("Create Docker Container") {
            steps {
				ansiblePlaybook playbook: '/var/lib/jenkins/workspace/66025010-nextjs/playbooks/deploy.yaml'
            }    
        } 
    }
}
