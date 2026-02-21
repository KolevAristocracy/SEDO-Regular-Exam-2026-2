pipeline{
    agent any
    tools {
        dotnetsdk 'dotnet6'
    }
    stages{
        stage("Restore Dependencies"){
            when {
                expression {
                    return env.GIT_BRANCH == 'origin/main'
                }
                
            }
            steps{
                sh "dotnet restore"
            }
        }

        stage("Build the app"){
            when {
                expression {
                    return env.GIT_BRANCH == 'origin/main'
                }
            }
            steps{
                sh "dotnet build --no-restore"
            }
        }
            
        stage("Run Tests"){
            when {
                expression {
                    return env.GIT_BRANCH == 'origin/main'
                }
            }
            steps{
                sh "dotnet test --no-build --verbosity normal"
            }
        }
    }
}