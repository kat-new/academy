# C01-AWS02

## Commands Execution Output

- Commands to create the S3 Bucket and to copy the file to the bucket:
```
aws s3 mb s3://c01-aws02-katnew-bucket-29042021 \
    --region ap-southeast-2
```

```
aws s3 cp \
    c01-aws02-katnew-file-29042021.txt \
    s3://c01-aws02-katnew-bucket-29042021
```

- Commands to allow the EC2 instance to access the files in S3:
```
aws iam create-policy \
    --policy-name EC2-S3Access-Policy \
    --policy-document file://PolicyDocument.json
    
    >>> arn:aws:iam::985318289922:policy/EC2-S3Access-Policy

aws iam create-role \
    --role-name EC2-S3Access-Role \
    --assume-role-policy-document file://AssumeRolePolicyDocument.json

    >>> arn:aws:iam::985318289922:role/EC2-S3Access-Role

aws iam attach-role-policy \
    --policy-arn arn:aws:iam::985318289922:policy/EC2-S3Access-Policy \
    --role-name EC2-S3Access-Role 
```

```
aws iam create-instance-profile \
    --instance-profile-name EC2-S3Access-Profile 

    >>> arn:aws:iam::985318289922:instance-profile/EC2-S3Access-Profile

aws iam add-role-to-instance-profile \
    --instance-profile-name EC2-S3Access-Profile \
    --role-name EC2-S3Access-Role
```

```
aws ec2 associate-iam-instance-profile \
    --instance-id i-0e9f9b578139809ec \
    --iam-instance-profile Name="EC2-S3Access-Profile"
```

- Commands to copy the S3 file to a folder inside the instance (executed from inside the EC2 Instance):

```
ssh -A ec2-user@ec2-52-64-25-206.ap-southeast-2.compute.amazonaws.com

aws configure

aws s3 cp s3://c01-aws02-katnew-bucket-29042021/c01-aws02-katnew-file-29042021.txt c01-aws02-katnew-file-29042021.txt
```


- Add a brief description of the challenges you faced:
```
If you manage your roles from the AWS CLI or the AWS API, you create roles and instance profiles as separate actions. Because roles and instance profiles can have different names, you must know the names of your instance profiles as well as the names of roles they contain. 
```

<!-- Don't change anything below this point-->
<!-- Before committing, remove both commented lines--> 
***
Answer for exercise [c01-aws02](https://github.com/devopsacademyau/academy/blob/635775538e8ad7793b305f48064b09e23c626fb7/classes/01class/exercises/c01-aws02/README.md)