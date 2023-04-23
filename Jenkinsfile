pipeline{
    agent any
    parameters{
        string(name: 'SPEC',defaultValue: "cypress/integration/**/**",description: "Enter the script path you want")
        choice(name: 'BROWSER', choices: ['chrome','edge','firefox'],description: "choice browser")
    }

    stages{
        stage('Building'){
            steps{
                echo "Building the application"
            }
        }
        stage('Testing'){
            steps{
                bat "npm i"
                bat "npx cypress run --browser ${BROWSER} --spec ${SPEC}"
            }
        }
    }

    post{
        always{
            publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: true, reportDir: 'cypress/report', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true])        
            }
    }
}
