pipeline {
    agent any
    stages {
        stage ('build') {
            steps {
                // Call a powershell script to build the application.
                // bat msbuild
                // Or
                // call a powershell script.
                // We have to determine if we want to keep the artifacts from the build, my gut says no since its not a huge project with many moving pieces.
                bat 'C:/Users/XboxDevProfile/.nuget/nuget.exe locals global-packages -clear'
                bat 'C:/Users/XboxDevProfile/.nuget/nuget.exe restore XboxTestApp.sln'
                bat 'msbuild XboxTestApp/XboxTestApp.csproj -property:Configuration=Debug -property:Platform=x64'
            }
        }
        /*stage ('test') {
            steps {
                // Run the UWP Unit test application again through a powershell script and succeed or fail based on the results.
                // Create a powershell script or something that will return non-zero on false.
            }
        }
        stage ('deploy') {
            steps {
                // Here we will run yet another powershell script that will copy the contents to a remote server where QA will be able to pull down the package.
                // Change
            }
        }*/
    }
}
