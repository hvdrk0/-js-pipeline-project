pipeline {
    agent any
    stages {
        stage("build") {
            when {
                expression {
                    env.GIT_BRANCH == 'origin/main'
                }
            }
            steps {
                echo 'building the application...(main)'
            }
        }
	stage("build2") {
	    when {
		expression {
		    env.GIT_BRANCH == 'origin/test'
		}
	    }
	    steps {
		echo 'building the application...(test)'
	    }
	}
        stage("test") {
            when {
                expression {
                    env.GIT_BRANCH == 'origin/test' || env.GIT_BRANCH == ''
                }
            }
            steps {
                echo 'testing the application...'
            }
        }
        stage("deploy") {
            steps {
                echo 'deploying the application...'
            }
        }
    }
}
