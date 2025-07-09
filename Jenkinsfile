pipeline {
    agent any
    stages {
          stage('Cleanup Workspace') {
            steps {
                cleanWs()
                bat """
                echo "Cleaned Up Workspace For Project"
                """
            }
        }
        stage(' Unit Testing') {
            steps {
                bat """
                echo "Running Unit Tests for the feature dev branch"
                """
            }
        }
        stage(' Unit Testing') {
            steps {
                bat """
                echo "Running Unit Tests for the develop dev branch"
                """
            }
        }
        stage(' Unit Testing') {
            steps {
                bat """
                echo "Running Unit Tests for the testing dev branch"
                """
            }
        }
      
        stage('Testing') {
            steps {
                echo "Running Unit Tests"
                bat 'scripts\\feature.bat'
            }
        }


        stage('Code Analysis') {
            steps {
                bat """
                echo "Running Code Analysis"
                """
            }
        }
          stage('Build Deploy Code') {
            when {
                branch 'develop'
            }
            steps {
                bat """
                echo "Building Artifact"
                """

                bat """
                echo "Deploying Code"
                """
            }
        }
          stage('Build Deploy Code for feature branch') {
            when {
                branch 'feature'
            }
            steps {
                bat """
                echo "Building Artifact for the feature branch"
                """

                bat """
                echo "Deploying Code for the feature branch"
                """
            }
        }

        stage('Deploy To Staging and Pre-Prod Code') {
            when {
                branch 'main'
            }
            steps {
                bat """
                echo "Building Artifact for Staging and Pre-Prod Environments"
                """
                bat """
                echo "Deploying to Staging Environment"
                """
                bat """
                echo "Deploying to Pre-Prod Environment"
                """
            }
        }
    }
}

