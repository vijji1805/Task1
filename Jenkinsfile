pipeline {
agent any

stages {
stage ('Deploy') {
steps{
sshagent(credentials : ['asg']) {
sh 'sh instances.sh > servers_list'
sh 'for word in $(cat servers_list); do ssh -t -t ubuntu@$word -o StrictHostKeyChecking=no sudo git -C /var/www/html pull; done'
}
}
}
}
}
