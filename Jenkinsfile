pipeline {
  agent any
  stages {
    stage('CodeQL Scan') {
      environment {
        GITHUB_CREDS = credentials('gh-jenkins') 
      }
      steps {
        sh '''
commit_id=`git rev-parse HEAD` 
refs_value=`git symbolic-ref HEAD`
/tmp/codeql-binaries/codeql-runner-linux init --repository rohitnb/one-more-scanner --github-url https://github.com --github-auth $GITHUB_CREDS_PSW --codeql-path /tmp/codeql-binaries/codeql/codeql
/tmp/codeql-binaries/codeql-runner-linux analyze --repository rohitnb/one-more-scanner --github-url https://github.com --github-auth $GITHUB_CREDS_PSW --commit $GIT_COMMIT --ref $refs_value'''
      }
    }

  }
}
