pipeline {
    agent any
    stages {
        stage ('build') {
            steps {
                // First clear the nuget packages.
                bat 'C:/Users/XboxDevProfile/.nuget/nuget.exe locals global-packages -clear'
                
                // Grab any dependencies 
                bat 'C:/Users/XboxDevProfile/.nuget/nuget.exe restore XboxTestApp.sln'
                bat 'msbuild XboxTestApp/XboxTestApp.csproj -property:AppxBundle=Always -property:Configuration=Debug -property:Platform=x64'
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
