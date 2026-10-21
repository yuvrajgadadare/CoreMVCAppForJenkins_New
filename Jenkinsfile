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
         stage("Deployment") {
            steps {
                // bat 'del /q /s "C:\\inetpub\\wwwroot\\WebApp\\"'
                // bat '"xcopy /E /Y /I "publish\\*" "C:\\inetpub\\wwwroot\\WebApp\\"'
                bat '''
                        if exist "C:\\inetpub\\wwwroot\\mvcapp" rmdir /q /s "C:\\inetpub\\wwwroot\\mvcapp"
                        mkdir "C:\\inetpub\\wwwroot\\mvcapp"
                    '''
                bat "C:\\Windows\\System32\\xcopy.exe /E /Y /I publish\\* C:\\inetpub\\wwwroot\\mvcapp\\"
            }
        }

    }
}