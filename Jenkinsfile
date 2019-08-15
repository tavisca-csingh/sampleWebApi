pipeline {
    agent any
    parameters {
        string(defaultValue: 'https://github.com/tavisca-csingh/sampleWebApi.git', name: 'GIT_SSH_PATH')
        string(defaultValue: 'WebApi.sln', name: 'SOLUTION_FILE_PATH')
        string(defaultValue: 'WebApi.Tests/WebApi.Tests.csproj', name: 'TEST_PROJECT_PATH')
    }
    stages {
        stage('Build') {
            steps {
                sh 'dotnet restore ${SOLUTION_FILE_PATH} --source https://api.nuget.org/v3/index.json',
                sh 'dotnet build  ${SOLUTION_FILE_PATH} -p:Configuration=release -v:n'
            }
        }
        stage('Test') {
            steps {
                sh 'dotnet test ${TEST_PROJECT_PATH}'
            }
        }
    }
}