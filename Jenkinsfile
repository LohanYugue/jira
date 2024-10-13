pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
    }

    post {
        always {

            script {
                // Envia informações do build para o Jira
                jiraSendBuildInfo(
                    site: 'lohan-petermann.atlassian.net' // Nome do site Jira configurado no Jenkins
                )
            }

            script {
                // Envia informações de deployment para o Jira
                jiraSendDeploymentInfo(
                    site: 'lohan-petermann.atlassian.net', // Nome do site Jira configurado no Jenkins
                    environmentId: 'main', // ID único do ambiente
                    environmentName: 'JIRA-1', // Nome do ambiente no Jira
                    environmentType: 'production', // Tipo do ambiente (production, staging, testing, etc.)
                    serviceIds: ['service-1'] // IDs de servico relevantes
                )
            }
        }
    }
}
