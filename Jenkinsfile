pipeline {
    agent any
    stages {
        stage ('build') {
            steps {
                // First clear the nuget packages.
                bat 'C:/Users/XboxDevProfile/.nuget/nuget.exe locals global-packages -clear'
                
                // Grab any dependencies 
                bat 'C:/Users/XboxDevProfile/.nuget/nuget.exe restore XboxTestApp.sln'
                bat 'msbuild XboxTestApp/XboxTestApp.csproj -property:AppxBundle=Always -property:AppxBundlePlatforms="x64" -property:Configuration=Debug -property:Platform=x64'
                bat 'msbuild XboxTestAppUnitTests/XboxTestAppUnitTests.csproj -property:AppxBundle=Always -property:AppxBundlePlatforms="x64" -property:Configuration=Debug -property:Platform=x64'
            }
        }
        /*stage ('test') {
            steps {
                // Build the test app.
                // Run the tests on the test app.       
                // bat 'vstest '
            }
        }
        /*stage ('deploy') {
            steps {
                // Here we will run yet another powershell script that will copy the contents to a remote server where QA will be able to pull down the package.
                // Change
            }
        }*/
    }
}
