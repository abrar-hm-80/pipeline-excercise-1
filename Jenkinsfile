pipeline {
  agent any
  stages {
    stage('Stage1') {
      steps {
        sh '''username="jenkins"
if [ `sed -n "/^$username/p" /etc/passwd` ]
then
    echo "User [$username] already exists"
else
    echo "User [$username] doesn\'t exist"
fi'''
      }
    }

    stage('Stage2') {
      steps {
        sh '''if test $(grep -c jenkins /etc/passwd) -ne 0
then
 sudo find /var/lib -user jenkins > /tmp/jenkins
fi'''
      }
    }

    stage('Stage3') {
      steps {
        sh '''for i in $(cat /tmp/jenkins)
do
ls -i $i
done
'''
      }
    }

  }
}