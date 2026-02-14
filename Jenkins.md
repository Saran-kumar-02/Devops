Jenkins & CI/CD 

Created custom Jenkins jobs and triggered jobs using other jobs. Ran a container using source code from Git via Jenkins. Used pipelines for the same workflow. 

Jenkins Insights 

(Detailed notes from jenkins.md) 

We usually put our code in a server online and it gets hosted and generates an IP. When code updates, we clone the whole new structure and remove the old one. If connected to hub, it automatically does this when pull is used, so the service is restarted. 

Architecture considerations: 

Single Tier vs 2 Tier vs 3 Tier architectures. 

All this can be automated using Jenkins. Step by step every job gets executed (Builds and Pipelines). 

A app gets developed -> Tested -> Packed -> Deployment. 

Jenkins Core: 

Main engine responsible for Web UI, Job Execution, Build Scheduling, Plugin Management, User Management. 

Can run shell commands (scripts). 

Important: To run a script like ./runmyresume.sh, you must give execution permission:  

sudo chmod +x runmyresume.sh 

Pipelines 

(from pipeline/pl.txt) 

A pipeline is one job that defines multiple stages/steps executed in order (or in parallel). 

Pipeline Script: 

pipeline{ 
   agent any 
   stages{ 
       stage('Print Hello'){ 
           steps{ 
               sh 'pwd' 
               git branch: 'main',url:' https://github.com/Saran-kumar-02/Devops.git ' 
               echo 'Hello' 
               sh 'ls' 
           } 
       } 
       stage('Docker'){ 
           steps{ 
               sh 'docker build -t web134 .' 
               sh 'docker run -d -p 5000:5000 web134' 
           } 
       } 
   } 
} 
