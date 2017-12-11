podTemplate(
    label: 'jnonino-docker-images',
    containers: [
	  containerTemplate(name: 'gradle', image: 'jnonino/jenkins-slave-gradle', ttyEnabled: true, command: 'cat'),
	  containerTemplate(name: 'maven', image: 'jnonino/jenkins-slave-maven', ttyEnabled: true, command: 'cat'),
	  containerTemplate(name: 'nodejs', image: 'jnonino/jenkins-slave-nodejs', ttyEnabled: true, command: 'cat'),
	  containerTemplate(name: 'python', image: 'jnonino/jenkins-slave-python', ttyEnabled: true, command: 'cat'),
	  containerTemplate(name: 'sonar-runner', image: 'jnonino/jenkins-slave-sonar-runner', ttyEnabled: true, command: 'cat')
    ]
)
{
    node('jnonino-docker-images') {

        stage('Build a Gradle project') {
            //git 'https://github.com/jenkinsci/kubernetes-plugin.git'
            container('gradle') {
                sh 'uname -a'
                sh 'gradle --version'
            }
        }

        stage('Build a Maven project') {
            //git 'https://github.com/jenkinsci/kubernetes-plugin.git'
            container('maven') {
                sh 'uname -a'
                sh 'mvn --version'
            }
        }

        stage('Build a Node.js project') {
            //git 'https://github.com/jenkinsci/kubernetes-plugin.git'
            container('nodejs') {
                sh 'uname -a'
                sh 'node --version'
		        sh 'npm --version'
            }
        }

        stage('Build a Python project') {
            //git 'https://github.com/jenkinsci/kubernetes-plugin.git'
            container('python') {
                sh 'uname -a'
                sh 'python --version'
		        sh 'pip --version'
            }
        }

        stage('Run Sonar Runner') {
            //git 'https://github.com/jenkinsci/kubernetes-plugin.git'
            container('sonar-runner') {
                sh 'uname -a'
                sh 'sonar-runner --version'
            }
        }
    }
}
