# c02-network05

## Commands Execution Output

- Commands for creating the internet gateway:
```
aws ec2 create-internet-gateway \
    --tag-specifications \
        'ResourceType=internet-gateway,Tags=[{Key=Name,Value=devopsacademy-igw}]' 

{
    "InternetGateway": {
        "Attachments": [],
        "InternetGatewayId": "igw-02b6bf5ddbb751858",
        "OwnerId": "985318289922",
        "Tags": [
            {
                "Key": "Name",
                "Value": "devopsacademy-igw"
            }
        ]
    }
}

```

```
aws ec2 attach-internet-gateway \
    --internet-gateway-id igw-02b6bf5ddbb751858 \
    --vpc-id vpc-0720661c365cb82b1
```

- Any extra challenges faced?

You must create the Gateway first, then attach it to the VPC.


<!-- Don't change anything below this point-->
***
Answer for exercise [c02-network05](https://github.com/devopsacademyau/academy/blob/893381c6f0b69434d9e8597d3d4b1c17f9bc1371/classes/02class/exercises/c02-network05/README.md)