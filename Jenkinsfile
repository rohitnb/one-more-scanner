pipeline {
  agent any
  stages {
    stage('CodeQL Scan') {
      environment {
        GITHUB_CREDS = credentials('gh-jenkins') #Save the GitHub PAT as an ENV_VAR
      }
      steps {
        sh '''
commit_id=`git rev-parse HEAD` #Get the Commit-ID - NEEDED.
refs_value=`git symbolic-ref HEAD` #Get the refs - NEEDED.
/tmp/codeql-binaries/codeql-runner-linux init --repository rohitnb/one-more-scanner --github-url https://github.com --github-auth $GITHUB_CREDS_PSW --codeql-path /tmp/codeql-binaries/codeql/codeql
/tmp/codeql-binaries/codeql-runner-linux analyze --repository rohitnb/one-more-scanner --github-url https://github.com --github-auth $GITHUB_CREDS_PSW --commit $GIT_COMMIT --ref $refs_valueF'''
      }
    }

  }
}
