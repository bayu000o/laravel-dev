node {
    checkout scm

    // Build
    stage("Build") {
        docker.image('php:8.4-cli').inside('--entrypoint= -u root') {
            sh 'apt-get update && apt-get install -y git zip unzip curl'
            sh 'curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer'
            sh 'composer install --no-scripts --no-interaction'
        }
    }

    // Testing
    stage("Test") {
        docker.image('ubuntu:24.04').inside('-u root') {
            sh 'echo "Ini adalah test"'
        }
    }

    // Deploy
    //stage("Deploy") {
        //sshagent(credentials: ['ssh-prod']) {
            //sh 'mkdir -p ~/.ssh'
            //sh 'ssh-keyscan -H "172.30.33.107" >> ~/.ssh/known_hosts'
            //sh 'rsync -rav --delete ./ kaptenstayy@172.30.33.107:/home/kaptenstayy/prod.kelasdevops.xyz/ --exclude=.env --exclude=storage --exclude=.git'
        //}
    //}
}