pipeline{
    agent any{
        tools {nodejs 'node-22'}
    }
     environment {
        VERCEL_TOKEN      = credentials('vercel-token')
        VERCEL_ORG_ID     = credentials('vercel-org-id')
        VERCEL_PROJECT_ID = credentials('vercel-project-id')
    }
    stages{
        stage('Install') {
           steps{ bat 'npm ci' }
        }
        stage('Lint') {
           steps{ bat 'npm lint' }
        }
        stage('build') {
           steps {bat 'npm run build'}
        }
        stage('Deploy To Vercel') {
           steps{ bat 'npx vercel deploy --prod --yes' }
        }
    }
}