pipeline {
    agent any

    stages {
        stage('Get Pull Request for Commit') {
            steps {
                script {
                    def githubToken = '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'
                    def repoOwner = 'abhigyanr8'
                    def repoName = 'Jenkins_Branch_Stage'
                    def commitSha = '4faf09a2fca5f88905542274bc2508'

                    def apiUrl = "https://api.github.com/repos/${repoOwner}/${repoName}/commits/${commitSha}/pulls"

                    def response = bat(script: """
                        curl -s -H "Authorization: Bearer ${githubToken}" ${apiUrl}
                    """, returnStatus: false).trim()

                    echo "Response from curl: ${response}"

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
