# sshca
Serverless SSH CA

* create a kms key in eu-west-1 with the alias bless
* create an instance profile with admin privileges
* start up an aws linux ec2 instance with that profile
* ssh into it
* sudo yum install gcc libffi-devel python-devel openssl-devel git
* git clone https://github.com/martinkaberg/sshca.git
* cd sshca
* sudo pip install -r requirments.txt
* bash create-on-aws-linux.sh





** Build **

I was not able to create a working zip file on my ubuntu laptop. Works fine on EC2 instance

make sure you have a kms key that your iam user/role can use Encrypt with. The alias of the key must be bless







** on server **

add too sshd config

TrustedUserCAKeys /etc/ssh/ca.pub
LogLevel VERBOSE


curl https://joxcu5vyr0.execute-api.eu-west-1.amazonaws.com/dev2/cert > /etc/ssh/ca.pub
chmod 0600 /etc/ssh/ca.pub
service sshd restart

** on client **

python scripts/get-cert.py --host joxcu5vyr0.execute-api.eu-west-1.amazonaws.com --public-key-file ~/.ssh/id_rsa.pub --stage dev2


