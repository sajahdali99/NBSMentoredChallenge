pipeline {
	agent any
	stages {
		stage("Perform SAST Testing with Sonarqube"){
			steps {
				sh "./home/student/NBSMentoredChallenge/scripts/sonarqube.sh"
			}
		}
		stage("Perform Unit Testing with pytest & pytest-cov"){
			steps {
				sh "./scripts/pytest.sh"
			}
		}
		stage("Build images with docker-compose"){
			steps{
				sh "./scripts/build.sh"
			}
		}
		stage("Tag & Push image to Nexus Repository 8082"){
			steps{
				sh "./scripts/push.sh"
			}
		}
		stage("Run containers with recently build images"){
			steps{
				sh "./scripts/run.sh"
			}
		}
	}
}
