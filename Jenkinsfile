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
    }
}