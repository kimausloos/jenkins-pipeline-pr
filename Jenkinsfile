pipeline {
    agent any
    triggers {
        eventTrigger jmespathQuery("repository.name=='puppet-monorepo'&&pull_request.merged='true'&&action='closed'")
    }
    stages {
        stage('Example') {
            steps {
                echo 'received Webhook'
            }
        }
    }
}
