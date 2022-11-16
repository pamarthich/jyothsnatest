pipeline {
    agent any
    parameters{
        choice(name: "stack", choices: ["SalesFinanceCSW", "DevFinanceCSW", "ProdFinanceCSW"])
        choice(name: "environment", choices: ["Prd", "Dev", "Uat", "Qa"])
        text(name: "stackID", defaultValue: "01")
        choice(name: "fileVersion", choices: ["current", "depricated"])
        text(name: "deployUsername", defaultValue: "wasadmin")
        password(name: "deployPassword", defaultValue: "SECRET", description: "enter wasadmin password")
        text(name: "mailTo", defaultValue: "admin@localhost")
        choice(name: "deploy", choices: ["All", "Odd", "Even" ])
    }
    stages {
        stage('Execute Master Script') {
            steps {
		        sh "chmod +x test.sh"
                sh ("./test.sh")
            }
        }
        stage('loadenv'){
            when {
                branch main
            }
            steps {
                load 'main_env.groovy'
                echo "$env.name"
                echo "$env.BRANCH"
            }
        }
        stage('loadenv'){
            when {
                branch dev
            }
            steps {
                load 'dev_env.groovy'
                echo "$env.name"
                echo "$env.BRANCH"
            }
        }

    }
}
