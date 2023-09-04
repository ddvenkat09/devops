pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                // Checkout code from Git repository (no credentials needed for public repository)
                git url: 'https://github.com/ddvenkat09/jenkins-example-scripts-php.git'
            }
        }
        stage('Update Nginx and Reload') {
            steps {
                script {
                    // Stop Nginx
                    sh 'sudo systemctl stop nginx'
                    
                    // Pull code updates to /var/www/html
                    sh 'cd /var/www/html && git pull'
                    
                    // Run cleanup scripts
                    sh 'cd /var/www/html && ./cleanup.sh'
                    
                    // Start Nginx
                    sh 'sudo systemctl start nginx'
                    
                    // Reload Nginx to apply configuration changes (if any)
                    sh 'sudo systemctl reload nginx'
                }
            }
        }
    }
}
