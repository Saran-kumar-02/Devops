Jenkins & CI/CD
Overview

Created custom Jenkins jobs

Triggered jobs using other Jenkins jobs

Ran Docker containers using source code from Git via Jenkins

Used Jenkins Pipelines for the same workflow

Jenkins Insights

(Detailed notes from jenkins.md)

Code is usually placed on an online server where it gets hosted and generates an IP address

When code updates:

The new structure is cloned

The old structure is removed

If Jenkins is connected to GitHub:

Using git pull automatically fetches updates

Services get restarted automatically

Architecture Considerations

Single Tier Architecture

Two Tier Architecture

Three Tier Architecture

All these architectures can be automated using Jenkins.

Jenkins Automation Flow

Step-by-step execution using Builds and Pipelines:

Application Development

Testing

Packaging

Deployment

Jenkins Core

Jenkins Core is the main engine responsible for:

Web UI

Job Execution

Build Scheduling

Plugin Management

User Management

Additional capabilities:

Can run shell commands (scripts)

Important Note (Script Execution Permission)

To run a script like:

./runmyresume.sh


Execution permission must be given:

sudo chmod +x runmyresume.sh

Jenkins Pipelines

(From pipeline/pl.txt)

What is a Pipeline?

A pipeline is a single Jenkins job

It defines multiple stages and steps

Stages can run sequentially or in parallel

Jenkins Pipeline Script Example
pipeline {
    agent any

    stages {

        stage('Print Hello') {
            steps {
                sh 'pwd'
                git branch: 'main', url: 'https://github.com/Saran-kumar-02/Devops.git'
                echo 'Hello'
                sh 'ls'
            }
        }

        stage('Docker') {
            steps {
                sh 'docker build -t web134 .'
                sh 'docker run -d -p 5000:5000 web134'
            }
        }

    }
}
