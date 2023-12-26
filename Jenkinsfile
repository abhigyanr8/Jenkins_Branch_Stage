pipeline {
    agent any
        stage('Get Pull Request for Commit') {
            steps {
                script {
                    def githubToken = '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'
                    def repoOwner = 'abhigyanr8'
                    def repoName = 'Jenkins_Branch_Stage'
                    def commitSha = '4faf09a2fca5f88905542274bc2508'

                    def apiUrl = "https://api.github.com/repos/abhigyanr8/Jenkins_Branch_Stage/commits/3cdbcaf/pulls"

                    def response = bat(script: """
                        curl -X GET ${apiUrl}
                    """, returnStatus: false)

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
