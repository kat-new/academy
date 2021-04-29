# C01-AWS01

## Commands Execution Output

- Commands to create the first EC2 instance and any additional resource required:
```
aws ec2 create-key-pair  \
    --key-name MyKeyPair \
    --query 'KeyMaterial' \
    --output text > MyKeyPair.pem 

```

```
myIpAddress=$(
    curl ipecho.net/plain ; echo
)

securityGroup=$( \
    aws ec2 create-security-group \
        --group-name my-sg \
        --description "My security group" \
        --query 'GroupId' \
        --output text \
)

aws ec2 authorize-security-group-ingress \
    --group-id $securityGroup \
    --protocol tcp \
    --port 22 \
    --cidr ${myIpAddress}/32

```

```
instanceId=$( \
    aws ec2 run-instances \
        --image-id resolve:ssm:/aws/service/ami-amazon-linux-latest/amzn2-ami-hvm-x86_64-gp2 \
        --instance-type t2.micro \
        --tag-specifications \
            'ResourceType=instance,Tags=[{Key=Name,Value=bastion-instance}]' \
        --key-name MyKeyPair \
        --security-group-ids $securityGroup \
        --associate-public-ip-address \
        --query 'Instances[0].InstanceId' \
        --output text \
)
```

- Commands to connect to the first EC2 instance:
```
aws ec2 describe-instance-status \
    --instance-ids $instanceId \
    --query 'InstanceStatuses[0].SystemStatus.Status' \
    --output text 
```

```
instancePublicDNS=$( \
    aws ec2 describe-instances \
        --instance-ids "$instanceId" \
        --query 'Reservations[0].Instances[0].PublicDnsName' \
        --output text \
)

chmod 400 MyKeyPair.pem
ssh-add -K MyKeyPair.pem

ssh -A ec2-user@${instancePublicDNS} -vvv

```

- Commands to create the second EC2 instance and any additional resource required:
```
instanceSubnetId=$( \
    aws ec2 describe-instances \
        --instance-ids "$instanceId" \
        --query 'Reservations[0].Instances[0].SubnetId' \
        --output text \
)

bastionInstanceIpAddress=$( \
    aws ec2 describe-instances \
        --instance-ids "$instanceId" \
        --query 'Reservations[0].Instances[0].PrivateIpAddress' \
        --output text \
)

privateSecurityGroup=$( \
    aws ec2 create-security-group \
        --group-name my-private-sg \
        --description "My private security group" \
        --query 'GroupId' \
        --output text \
)

aws ec2 authorize-security-group-ingress \
    --group-id $privateSecurityGroup \
    --protocol tcp \
    --port 22 \
    --cidr ${bastionInstanceIpAddress}/32

privateInstanceId=$( \
    aws ec2 run-instances \
        --image-id resolve:ssm:/aws/service/ami-amazon-linux-latest/amzn2-ami-hvm-x86_64-gp2 \
        --instance-type t2.micro \
        --tag-specifications \
            'ResourceType=instance,Tags=[{Key=Name,Value=private-instance}]' \
        --key-name MyKeyPair \
        --security-group-ids $privateSecurityGroup \
        --subnet-id $instanceSubnetId \
        --no-associate-public-ip-address \
        --query 'Instances[0].InstanceId' \
        --output text \
)
```

- Commands to connect to the second EC2 instance:
```
aws ec2 describe-instances \
    --instance-ids "$privateInstanceId" \
    --query 'Reservations[0].Instances[0].PrivateDnsName' \
    --output text
```

```
ssh -A ec2-user@${instancePublicDNS}

ssh ec2-user@ip-172-31-10-66.ap-southeast-2.compute.internal

```

***
Answer for exercise [c01-aws01](https://github.com/devopsacademyau/academy/blob/635775538e8ad7793b305f48064b09e23c626fb7/classes/01class/exercises/c01-aws01/README.md)