pipeline {
    agent {
        label 'dotnet'
    }
    options {
        timeout (time: 1, unit: 'HOURS')
    }
    triggers {
        pollSCM ('* * * * *')
    }

    stages {
        stage ('SCM') {
            steps {
                git url: 'https://github.com/dummyrepos/nopCommerceaug24.git',
                    branch: 'develop'    
            }      
        }
        stage ('BUILD') {
            steps {
                sh 'dotnet build --configuration Release src/Presentation/Nop.Web/Nop.Web.csproj'
                sh 'mkdir published && dotnet publish -o ./published -c Release src/Presentation/Nop.Web/Nop.Web.csproj'
            }
        }
    }
}