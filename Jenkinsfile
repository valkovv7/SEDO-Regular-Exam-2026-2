pipeline {
    agent {
        docker {
            image 'mcr.microsoft.com/dotnet/sdk:6.0'
            args '-u root'
        }
    }

    stages {
        stage('Checkout the repository') {
		    when {
                expression {
					return env.GIT_BRANCH == 'origin/main'
				}
            }
            steps {
                checkout scm
            }
        }

        stage('Restore dependencies') {
			when {
                expression {
					return env.GIT_BRANCH == 'origin/main'
				}
            }
            steps {
                sh 'dotnet restore'
            }
        }

        stage('Build the app') {
			when {
                expression {
					return env.GIT_BRANCH == 'origin/main'
				}
            }
            steps {
                sh 'dotnet build --no-restore'
            }
        }

        stage('Test the app') {
			when {
                expression {
					return env.GIT_BRANCH == 'origin/main'
				}
            }
            steps {
                sh 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
