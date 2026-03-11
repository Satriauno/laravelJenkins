node {
    // Fix PATH for this pipeline
    environment {
        PATH+EXTRA = '/usr/local/bin:/opt/homebrew/bin:/usr/bin:/bin'
    }
    
    checkout scm

    // Debug: verify environment
    stage('Debug') {
        steps {
            sh 'echo "=== PATH ==="'
            sh 'echo $PATH'
            sh 'echo "=== which docker ==="'
            sh 'which docker || echo "docker NOT FOUND"'
            sh 'docker --version || echo "docker command FAILED"'
        }
    }

    stage("Build") {
        docker.image('shippingdocker/php-composer:7.4').inside('-u root') {
            sh 'rm -f composer.lock'
            sh 'composer install'
        }
    }

    stage("Testing") {
        docker.image('ubuntu').inside('-u root') {
            sh 'echo "Ini adalah test"'
        }
    }
}