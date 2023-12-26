pipeline {
    agent any

    stages {
        stage('Get Pull Request for Commit') {
            steps {
                script {
                    def githubToken = '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'
                    def repoOwner = 'abhigyanr8'
                    def repoName = 'Jenkins_Branch_Stage'
                    def commitSha = ' 97e539297f4faf09a2fca5f88905542274bc2508

                    def apiUrl = "https://api.github.com/repos/${repoOwner}/${repoName}/commits/${commitSha}/pulls"

                    def response = sh(script: "curl -s -H 'Authorization: Bearer ${githubToken}' ${apiUrl}", returnStdout: true).trim()

                    // Parse JSON response
                    def pullRequests = readJSON text: response

                    if (pullRequests.size() > 0) {
                        def prNumber = pullRequests[0].number
                        echo "Pull Request associated with commit: ${prNumber}"
                    } else {
                        echo "No pull request found for the commit."
                    }
                }
            }
        }
    }
}
