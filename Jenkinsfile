podTemplate(
    label: 'cnservices-docker-images',
    nodeUsageMode: 'EXCLUSIVE',
    activeDeadlineSeconds: 60,
    containers: [
	  containerTemplate(name: 'gradle', image: 'cnservices/jenkins-slave-gradle', ttyEnabled: true, command: 'cat'),
	  containerTemplate(name: 'maven', image: 'cnservices/jenkins-slave-maven', ttyEnabled: true, command: 'cat'),
	  containerTemplate(name: 'nodejs', image: 'cnservices/jenkins-slave-nodejs', ttyEnabled: true, command: 'cat'),
	  containerTemplate(name: 'python', image: 'cnservices/jenkins-slave-python', ttyEnabled: true, command: 'cat'),
	  containerTemplate(name: 'sonar', image: 'cnservices/jenkins-slave-sonar-runner', ttyEnabled: true, command: 'cat'),
	  containerTemplate(name: 'docker', image: 'docker', ttyEnabled: true, command: 'cat', privileged: true)
    ],
    volumes: [
        hostPathVolume(hostPath: '/var/run/docker.sock', mountPath: '/var/run/docker.sock')
    ]
)
{
    node('cnservices-docker-images') {

        stage('Build a Gradle project') {
            //git 'https://github.com/jenkinsci/kubernetes-plugin.git'
            container('gradle') {
                sh 'uname -a'
                sh 'java -version'
                sh 'javac -version'
                sh 'gradle --version'
            }
        }

        stage('Build a Maven project') {
            container('maven') {
                sh 'uname -a'
                sh 'java -version'
                sh 'javac -version'
                sh 'mvn --version'
            }
        }

        stage('Build a Node.js project') {
            container('nodejs') {
                sh 'uname -a'
                sh 'node --version'
		        sh 'npm --version'
            }
        }

        stage('Build a Python project') {
            container('python') {
                sh 'uname -a'
                sh 'python --version'
		        sh 'pip --version'
            }
        }

        stage('Run Sonar Runner') {
            container('sonar') {
                sh 'uname -a'
                sh 'sonar-runner --version'
            }
        }
	  
	  stage('Build echo image') {
            checkout scm
            container('docker') {
                sh 'docker build -t echo echo/'
                sh 'docker run echo'
            }
        }

        stage('Build ls image') {
            checkout scm
            container('docker') {
                sh 'docker build -t ls ls/'
                sh 'docker run ls'
            }
        }
    }
}
