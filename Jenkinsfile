pipeline {
    agent any

    stages {
         stage('To check whether PR Raised on Develop Branch') {
            steps {
                script {
                    def extractOrgAndRepo = { gitUrl ->
                        def matcher = gitUrl =~ /https?:\/\/github\.com\/([^\/]+)\/([^\/]+)\.git/
                        return matcher ? [matcher[0][1], matcher[0][2]] : [null, null]
                    }
                    def gitUrl ="https://github.anaplan.com/core-platform/core-sizing.git"
                    def (org, repo) = extractOrgAndRepo(gitUrl)
                    echo "Org: ${org}"
                    echo "Repo: ${repo}"

                    // Add additional steps or logic here
                }
            }
        }
        // stage('Get Pull Request for Commit') {
        //     steps {
        //         script {
        //             def githubToken = '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'
        //             def repoOwner = 'abhigyanr8'
        //             def repoName = 'Jenkins_Branch_Stage'
        //             def commitSha = '4faf09a2fca5f88905542274bc2508'

        //             def apiUrl = "  https://api.github.com/repos/abhigyanr8/Jenkins_Branch_Stage/commits/3cdbcaf/pulls"
                    
        //             def response
                    
        //              response = bat(script: """
        //                 curl -X GET ${apiUrl}
        //             """, returnStdout: true).trim()
        //             echo "Raw response: ${response}" 
        //             // Print the raw response for debugging

        //             def jsonResponse = response.substring(response.indexOf("["))
        //            echo "Raw response: ${jsonResponse}"
                  

        //             try {
        //                  def parser = new groovy.json.JsonSlurper()
        //                  def pullRequests = parser.parseText(jsonResponse)
        //                 // Try parsing the JSON string
        //               // def pullRequests = new groovy.json.JsonSlurper().parseText(response)


        //                 if (pullRequests.size() > 0) {
        //                     def prNumber = pullRequests[0].number
        //                     def branch = pullRequests[0].base.ref
        //                     echo "Pull Request associated with commit: ${prNumber}"
        //                     echo "Base branch of pull request: ${branch}"
        //                 } else {
        //                     echo "No pull request found for the commit."
        //                 }
        //             } catch (Exception e) {
        //                 echo "Error parsing JSON: ${e.message}"
        //                 // Handle the exception or add more debugging information as needed
        //             }
        //         }
        //     }
        // }
    }
}
