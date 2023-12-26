pipeline {
    agent any

    stages {
        stage('Get Pull Request for Commit') {
            steps {
                script {
                    def githubToken = 'your-github-token'
                    def repoOwner = 'your-repo-owner'
                    def repoName = 'your-repo-name'
                    def commitSha = '4faf09a2fca5f88905542274bc2508'

                    def apiUrl = "https://api.github.com/repos/${repoOwner}/${repoName}/commits/${commitSha}/pulls"

                    def response = sh(script: """
                        curl -s -H 'Authorization: Bearer ${githubToken}' ${apiUrl}
                    """, returnStdout: true).trim()

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
