pipeline {
    agent any
    stages {      
        stage("Copy file to Docker server"){
            steps {
				//แก้ตรง 66024963-html ให้เป็นชื่อเดียวกับ pipeline job/item ที่สร้างใน jenkins
                sh "scp -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null -r  /var/lib/jenkins/workspace/66024963-html/* root@43.209.4.218:~/66024963-html"
            }
        }
        
        stage("Build Docker Image") {
            steps {
                //path yaml files
				ansiblePlaybook playbook: '/var/lib/jenkins/workspace/66024963-html/playbooks/build.yaml'
            }    
        } 
        
        stage("Create Docker Container") {
            steps {
                //path yaml files
				ansiblePlaybook playbook: '/var/lib/jenkins/workspace/66024963-html/playbooks/deploy.yaml'
            }    
        } 
    }
}
