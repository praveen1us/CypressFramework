pipeline{
    agent any
    parameters{
        string(name: 'SPEC',defaultValuw: "cypress/integration/**/**",description: "Enter the script path you want")
        choice(name 'BROWSER', choices: ['chrome','edge','firefox'],descriotion: "choice browser")
    }

    options{
        ansiColor('xterm')
    }

    stages{
        stage("Building"){
            echo "Building the application"
        }
        stage("Testing"){
            steps{
                bat "npn i"
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
