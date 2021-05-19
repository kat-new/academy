# c02-network04

## Commands Execution Output

- Commands for creating the subnets:
```
aws ec2 create-subnet \
    --vpc-id vpc-0720661c365cb82b1 \
    --availability-zone ap-southeast-2a \
    --cidr-block 10.0.0.0/24 \
    --tag-specifications \
        'ResourceType=subnet,Tags=[{Key=Name,Value=private-a}]' 

{
    "Subnet": {
        "AvailabilityZone": "ap-southeast-2a",
        "AvailabilityZoneId": "apse2-az3",
        "AvailableIpAddressCount": 251,
        "CidrBlock": "10.0.0.0/24",
        "DefaultForAz": false,
        "MapPublicIpOnLaunch": false,
        "State": "available",
        "SubnetId": "subnet-0c7203e6a0860e521",
        "VpcId": "vpc-0720661c365cb82b1",
        "OwnerId": "985318289922",
        "AssignIpv6AddressOnCreation": false,
        "Ipv6CidrBlockAssociationSet": [],
        "Tags": [
            {
                "Key": "Name",
                "Value": "private-a"
            }
        ],
        "SubnetArn": "arn:aws:ec2:ap-southeast-2:985318289922:subnet/subnet-0c7203e6a0860e521"
    }
}
```

```
aws ec2 create-subnet \
    --vpc-id vpc-0720661c365cb82b1 \
    --availability-zone ap-southeast-2b \
    --cidr-block 10.0.128.0/24 \
    --tag-specifications \
        'ResourceType=subnet,Tags=[{Key=Name,Value=private-b}]' 

{
    "Subnet": {
        "AvailabilityZone": "ap-southeast-2b",
        "AvailabilityZoneId": "apse2-az1",
        "AvailableIpAddressCount": 251,
        "CidrBlock": "10.0.128.0/24",
        "DefaultForAz": false,
        "MapPublicIpOnLaunch": false,
        "State": "available",
        "SubnetId": "subnet-061e60329a5f4a688",
        "VpcId": "vpc-0720661c365cb82b1",
        "OwnerId": "985318289922",
        "AssignIpv6AddressOnCreation": false,
        "Ipv6CidrBlockAssociationSet": [],
        "Tags": [
            {
                "Key": "Name",
                "Value": "private-b"
            }
        ],
        "SubnetArn": "arn:aws:ec2:ap-southeast-2:985318289922:subnet/subnet-061e60329a5f4a688"
    }
}
```

```
aws ec2 create-subnet \
    --vpc-id vpc-0720661c365cb82b1 \
    --availability-zone ap-southeast-2c \
    --cidr-block 10.0.192.0/24 \
    --tag-specifications \
        'ResourceType=subnet,Tags=[{Key=Name,Value=private-c}]' 
 
{
    "Subnet": {
        "AvailabilityZone": "ap-southeast-2c",
        "AvailabilityZoneId": "apse2-az2",
        "AvailableIpAddressCount": 251,
        "CidrBlock": "10.0.192.0/24",
        "DefaultForAz": false,
        "MapPublicIpOnLaunch": false,
        "State": "available",
        "SubnetId": "subnet-0e9340f9f478ed095",
        "VpcId": "vpc-0720661c365cb82b1",
        "OwnerId": "985318289922",
        "AssignIpv6AddressOnCreation": false,
        "Ipv6CidrBlockAssociationSet": [],
        "Tags": [
            {
                "Key": "Name",
                "Value": "private-c"
            }
        ],
        "SubnetArn": "arn:aws:ec2:ap-southeast-2:985318289922:subnet/subnet-0e9340f9f478ed095"
    }
}
```

```
aws ec2 create-subnet \
    --vpc-id vpc-0720661c365cb82b1 \
    --availability-zone ap-southeast-2a \
    --cidr-block 10.0.64.0/24 \
    --tag-specifications \
        'ResourceType=subnet,Tags=[{Key=Name,Value=public-a}]' 

{
    "Subnet": {
        "AvailabilityZone": "ap-southeast-2a",
        "AvailabilityZoneId": "apse2-az3",
        "AvailableIpAddressCount": 251,
        "CidrBlock": "10.0.64.0/24",
        "DefaultForAz": false,
        "MapPublicIpOnLaunch": false,
        "State": "available",
        "SubnetId": "subnet-004169e31a0253465",
        "VpcId": "vpc-0720661c365cb82b1",
        "OwnerId": "985318289922",
        "AssignIpv6AddressOnCreation": false,
        "Ipv6CidrBlockAssociationSet": [],
        "Tags": [
            {
                "Key": "Name",
                "Value": "public-a"
            }
        ],
        "SubnetArn": "arn:aws:ec2:ap-southeast-2:985318289922:subnet/subnet-004169e31a0253465"
    }
}
```

```
aws ec2 create-subnet \
    --vpc-id vpc-0720661c365cb82b1 \
    --availability-zone ap-southeast-2b \
    --cidr-block 10.0.76.0/24 \
    --tag-specifications \
        'ResourceType=subnet,Tags=[{Key=Name,Value=public-b}]' 

{
    "Subnet": {
        "AvailabilityZone": "ap-southeast-2b",
        "AvailabilityZoneId": "apse2-az1",
        "AvailableIpAddressCount": 251,
        "CidrBlock": "10.0.76.0/24",
        "DefaultForAz": false,
        "MapPublicIpOnLaunch": false,
        "State": "available",
        "SubnetId": "subnet-0bf9ddd3baf60d118",
        "VpcId": "vpc-0720661c365cb82b1",
        "OwnerId": "985318289922",
        "AssignIpv6AddressOnCreation": false,
        "Ipv6CidrBlockAssociationSet": [],
        "Tags": [
            {
                "Key": "Name",
                "Value": "public-b"
            }
        ],
        "SubnetArn": "arn:aws:ec2:ap-southeast-2:985318289922:subnet/subnet-0bf9ddd3baf60d118"
    }
}
```

```
aws ec2 create-subnet \
    --vpc-id vpc-0720661c365cb82b1 \
    --availability-zone ap-southeast-2c \
    --cidr-block 10.0.180.0/24 \
    --tag-specifications \
        'ResourceType=subnet,Tags=[{Key=Name,Value=public-c}]' 

{
    "Subnet": {
        "AvailabilityZone": "ap-southeast-2c",
        "AvailabilityZoneId": "apse2-az2",
        "AvailableIpAddressCount": 251,
        "CidrBlock": "10.0.180.0/24",
        "DefaultForAz": false,
        "MapPublicIpOnLaunch": false,
        "State": "available",
        "SubnetId": "subnet-039e2737426c5c8c1",
        "VpcId": "vpc-0720661c365cb82b1",
        "OwnerId": "985318289922",
        "AssignIpv6AddressOnCreation": false,
        "Ipv6CidrBlockAssociationSet": [],
        "Tags": [
            {
                "Key": "Name",
                "Value": "public-c"
            }
        ],
        "SubnetArn": "arn:aws:ec2:ap-southeast-2:985318289922:subnet/subnet-039e2737426c5c8c1"
    }
}
```

- Any extra challenges faced?


<!-- Don't change anything below this point-->
***
Answer for exercise [c02-network04](https://github.com/devopsacademyau/academy/blob/893381c6f0b69434d9e8597d3d4b1c17f9bc1371/classes/02class/exercises/c02-network04/README.md)