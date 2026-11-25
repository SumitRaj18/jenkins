pipeline {
    agent any

    tools { nodejs 'node-22' }

    environment {
        VERCEL_TOKEN      = credentials('vercel-token')
        VERCEL_ORG_ID     = credentials('vercel-org-id')
        VERCEL_PROJECT_ID = credentials('vercel-project-id')
    }

    stages {
        stage('Install') {
            steps { dir('my-app') { bat 'npm ci' } }
        }
        stage('Lint') {
            steps { dir('my-app') { bat 'npm run lint' } }
        }
        stage('Build') {
            steps { dir('my-app') { bat 'npm run build' } }
        }
        stage('Deploy to Vercel-App') {
            steps { bat 'npx vercel deploy --prod --yes' }
        }
    }
}