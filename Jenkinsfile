pipeline {
    agent any
    stages {
        stage ('build') {
            steps {
                // Grab any dependencies
                bat 'C:/Users/XboxDevProfile/.nuget/nuget.exe locals all -Clear'
                bat 'C:/Users/XboxDevProfile/.nuget/nuget.exe restore XboxTestApp.sln'
                bat 'msbuild XboxTestApp/XboxTestApp.csproj -property:AppxBundle=Always -property:AppxBundlePlatforms="x64" -property:Configuration=Debug -property:Platform=x64'
                bat 'msbuild XboxTestAppUnitTests/XboxTestAppUnitTests.csproj -property:AppxBundlePlatforms="x64" -property:Configuration=Release'
            }
        }
        stage ('test') {
            steps {
                // Install the certificate for the test app.
                bat '"C:/Program Files (x86)/Windows Kits/10/bin/10.0.17763.0/x64/certmgr.exe" /add "C:/Users/XboxDevProfile/Developement/XboxTestApp/XboxTestAppUnitTests/AppPackages/XboxTestAppUnitTests_1.0.0.0_x86_Test/XboxTestAppUnitTests_1.0.0.0_x86.cer" /s /r localMachine trustedPeople'
                
                powershell 'Remove-AppxPackage -Package XboxTestAppUnitTests_1.0.0.0_x86.appx'
                
                // Run the tests on the test app.       
                bat '"C:/Users/XboxDevProfile/Developement/XboxTestApp/XboxTestAppUnitTests/AppPackages/XboxTestAppUnitTests_1.0.0.0_x86_Test/XboxTestAppUnitTests_1.0.0.0_x86.appx"'
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
