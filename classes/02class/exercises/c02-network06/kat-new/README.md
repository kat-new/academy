# c02-network06

## Commands Execution Output

- Commands for creating the NAT gateway:
```
elasticIp=$( \
    aws ec2 allocate-address \
        --query 'AllocationId' \
        --output text 
)
```

```
aws ec2 create-nat-gateway \
    --subnet-id subnet-004169e31a0253465 \
    --allocation-id $elasticIp \
    --tag-specifications \
        'ResourceType=natgateway,Tags=[{Key=Name,Value=devopsacademy-ngw}]' 
        
{
    "ClientToken": "9ab493a6-6df7-4085-8868-b48563fcfa4f",
    "NatGateway": {
        "CreateTime": "2021-05-21T09:49:28+00:00",
        "NatGatewayAddresses": [
            {
                "AllocationId": "eipalloc-04ab42dfa52390b93"
            }
        ],
        "NatGatewayId": "nat-05dcc5d7e2c153450",
        "State": "pending",
        "SubnetId": "subnet-004169e31a0253465",
        "VpcId": "vpc-0720661c365cb82b1",
        "Tags": [
            {
                "Key": "Name",
                "Value": "devopsacademy-ngw"
            }
        ]
    }
}       
```

- Any extra challenges faced?

Before you can use an Elastic IP address, you must allocate it to your account.

<!-- Don't change anything below this point-->
***
Answer for exercise [c02-network06](https://github.com/devopsacademyau/academy/blob/893381c6f0b69434d9e8597d3d4b1c17f9bc1371/classes/02class/exercises/c02-network06/README.md)