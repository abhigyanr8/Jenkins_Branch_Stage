#!/usr/bin/groovy
@Library('HTTP-Request') _

pipeline {
    agent any

    stages {
        stage('Fetch PR Details') {
            steps {
                script {
                    // Replace these variables with your actual values
                    def githubApiUrl = "https://api.github.com/abhigyanr8/Jenkins_Branch_Stage.gitpulls"
                    def githubToken = "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"
                    def commitSha = "d6f7963f271c901f1fbae14c388db41c2961b08a"

                    def prDetails = getPullRequestDetails(githubApiUrl, githubToken, commitSha)

                    echo "PR Number: ${prDetails.number}"
                    echo "Title: ${prDetails.title}"
                    echo "Body: ${prDetails.body}"
                    echo "Target Branch: ${prDetails.base.ref}"
                }
            }
        }
    }
}

def getPullRequestDetails(githubApiUrl, githubToken, commitSha) {
    def apiUrl = "${githubApiUrl}?head=abhigyanr8:master&state=all"  // Adjust the 'head' parameter accordingly

    def response = httpRequest(
        httpMode: 'GET',
        url: apiUrl,
        authentication: 'your-github-credentials-id',  // Set your GitHub credentials ID
        customHeaders: [[name: 'Authorization', value: "Bearer ${githubToken}"]]
    )

    def prDetails = response.data.find { it.head.sha == commitSha }
    return prDetails
}
