pipeline{
agent any
stages{
stage("maven site"){
steps{
sh "mvn -f /root/my-app/pom.xml clean package"
sh "mvn -f /root/my-app/pom.xml site"
}
}
stage("deploy-httpd"){
steps{
sh """
scp -r -o StrictHostKeyChecking=no /root/my-app/target/site/* 192.168.1.13:/var/www/html/
ssh root@192.168.1.13 systemctl restart httpd
"""
}
}
}
}
