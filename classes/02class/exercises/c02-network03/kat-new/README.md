# c02-network03

## Commands Execution Output

- Commands for creating a new VPC:
```
aws ec2 create-vpc \
    --cidr-block 10.0.0.0/16 \
    --no-amazon-provided-ipv6-cidr-block \
    --instance-tenancy default \
    --tag-specifications \
        'ResourceType=vpc,Tags=[{Key=Name,Value=devopsacademy-vpc}]' 
```

```
{
    "Vpc": {
        "CidrBlock": "10.0.0.0/16",
        "DhcpOptionsId": "dopt-adb9b2ca",
        "State": "pending",
        "VpcId": "vpc-0720661c365cb82b1",
        "OwnerId": "985318289922",
        "InstanceTenancy": "default",
        "Ipv6CidrBlockAssociationSet": [],
        "CidrBlockAssociationSet": [
            {
                "AssociationId": "vpc-cidr-assoc-09fe932b117d6a53b",
                "CidrBlock": "10.0.0.0/16",
                "CidrBlockState": {
                    "State": "associated"
                }
            }
        ],
        "IsDefault": false,
        "Tags": [
            {
                "Key": "Name",
                "Value": "devopsacademy-vpc"
            }
        ]
    }
}
```

- Any extra challenges faced?
No extra challenges, maybe I did it wrong? :sweat_smile:


<!-- Don't change anything below this point-->
***
Answer for exercise [c02-network03](https://github.com/devopsacademyau/academy/blob/893381c6f0b69434d9e8597d3d4b1c17f9bc1371/classes/02class/exercises/c02-network03/README.md)