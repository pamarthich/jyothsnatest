pipeline {
    agent any
    stages {
        stage('Execute Master Script') {
            steps {
		sh "chmod +x test.sh"
                sh ('./test.sh')
            }
        }
    }
}
