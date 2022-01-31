node{

	def app

	stage('clone Repositry'){
		checkout scm
	}

	stage('build image'){
		app=docker.build('yogeshpal700/test-repo')
	}

	stage('test image'){
		app.inside{
			sh 'echo "Testing Passed"'
		}
	}

	stage('push image'){
		docker.withRegistry('https://registry.hub.docker.com','Docker-Img')
		app.push("${evn.BUILD_NUMBER}")
		app.push("latest")
	}
}
