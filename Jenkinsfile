pipeline {
    agent any
    environment {
        // DOTNET_CLI_HOME= "C:\\Program Files\\dotnet"
        DOTNET_CLI_HOME="DotNetCore"
    }
    stages {
        stage("Checkout") {
            steps {
                checkout scm
            }
        }
        stage("Restore") {
            steps {
                bat "dotnet restore CoreMVCAppForJenkins.slnx"
            }
        }
        stage("Build") {
            steps {
                bat "dotnet build CoreMVCAppForJenkins.slnx --configuration Release"
            }
        }
        stage("Test") {
            steps {
                bat "dotnet test --no-restore --configuration Release"
            }
        }
        stage("Publish") {
            steps {
                 bat "dotnet publish --no-restore --configuration Release --output .\\publish"

            }
        }
    }
}