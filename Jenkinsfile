pipeline {
  agent any
  stages {
    stage('CodeQL Scan') {
      environment {
        GITHUB_CREDS = credentials('gh-jenkins') 
      }
      steps {
        sh '''
if [ -z "$CHANGE_ID" ]
then
      $GIT_REF="refs/pull/PR-$CHANGE_ID/head"
else
      $GIT_REF=`git symbolic-ref HEAD`
fi
/tmp/codeql-binaries/codeql-runner-linux init --repository rohitnb/one-more-scanner --github-url https://github.com --github-auth $GITHUB_CREDS_PSW --codeql-path /tmp/codeql-binaries/codeql/codeql
/tmp/codeql-binaries/codeql-runner-linux analyze --repository rohitnb/one-more-scanner --github-url https://github.com --github-auth $GITHUB_CREDS_PSW --commit $GIT_COMMIT --ref $GIT_REF'''
      }
    }

  }
}
