node {
    checkout scm
    
    withEnv(['PATH+EXTRA=/usr/local/bin:/opt/homebrew/bin']) {
        
        stage("Build") {
            docker.image('composer:2.6').inside('-u root') {
                sh 'rm -f composer.lock'
                sh 'composer install --no-interaction --prefer-dist'
            }
        }

        stage("Testing") {
            docker.image('php:7.4-cli-alpine').inside('-u root') {
                sh 'echo "Ini adalah test"'
            }
        }
    }
}