pipeline {
  agent any

  stages {
    stage('Branch Info') {
      steps {
        echo "Current branch: ${env.BRANCH_NAME}"
      }
    }

    stage('Run only on bug-fix') {
      when {
        branch 'bug-fix'
      }
      steps {
        echo "✅ Running this stage on bug-fix branch!"
        // bat 'ruff test.py'  // or `sh` if on Linux
      }
    }

    stage('Default fallback') {
      when {
        not {
          branch 'bug-fix'
        }
      }
      steps {
        echo "⚠️ This is not bug-fix branch. Skipping core logic."
      }
    }
  }

  post {
    always {
      echo "Pipeline finished on ${env.BRANCH_NAME}"
    }
  }
}
