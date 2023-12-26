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

                    def apiUrl = "  https://api.github.com/repos/abhigyanr8/Jenkins_Branch_Stage/commits/3cdbcaf/pulls"
                    
                    def response
                    
                     response = bat(script: """
                        curl -X GET ${apiUrl}
                    """, returnStdout: true).trim()
                    echo "Raw response: ${response}" // Print the raw response for debugging

                    try {
                        // Try parsing the JSON string
                       def pullRequests = new groovy.json.JsonSlurper().parseText(response)


                        if (pullRequests.size() > 0) {
                            def prNumber = pullRequests[0].number
                            echo "Pull Request associated with commit: ${prNumber}"
                        } else {
                            echo "No pull request found for the commit."
                        }
                    } catch (Exception e) {
                        echo "Error parsing JSON: ${e.message}"
                        // Handle the exception or add more debugging information as needed
                    }
                }
            }
        }
    }
}