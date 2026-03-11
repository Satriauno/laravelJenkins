node {
    checkout scm

    // Debug: verify environment
    stage('Debug') {
        withEnv(['PATH+EXTRA=/usr/local/bin:/opt/homebrew/bin']) {
            sh 'echo "=== PATH ==="'
            sh 'echo $PATH'
            sh 'which docker || echo "docker NOT FOUND"'
            sh 'docker --version || echo "docker command FAILED"'
        }
    }

    stage("Build") {
        withEnv(['PATH+EXTRA=/usr/local/bin:/opt/homebrew/bin']) {
            docker.image('shippingdocker/php-composer:7.4').inside('-u root') {
                sh 'rm -f composer.lock'
                sh 'composer install'
            }
        }
    }

    stage("Testing") {
        withEnv(['PATH+EXTRA=/usr/local/bin:/opt/homebrew/bin']) {
            docker.image('ubuntu').inside('-u root') {
                sh 'echo "Ini adalah test"'
            }
        }
    }
}