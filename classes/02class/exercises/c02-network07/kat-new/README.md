# c02-network07

## Commands Execution Output

- Commands for creating the route tables:
```
aws ec2 create-route-table \
    --vpc-id vpc-0720661c365cb82b1 \
    --tag-specifications \
        'ResourceType=route-table,Tags=[{Key=Name,Value=devopsacademy-rt-public}]' 

{
    "RouteTable": {
        "Associations": [],
        "PropagatingVgws": [],
        "RouteTableId": "rtb-097cac5fa2f7c02cb",
        "Routes": [
            {
                "DestinationCidrBlock": "10.0.0.0/16",
                "GatewayId": "local",
                "Origin": "CreateRouteTable",
                "State": "active"
            }
        ],
        "Tags": [
            {
                "Key": "Name",
                "Value": "devopsacademy-rt-public"
            }
        ],
        "VpcId": "vpc-0720661c365cb82b1",
        "OwnerId": "985318289922"
    }
}
```
```
aws ec2 create-route-table \
    --vpc-id vpc-0720661c365cb82b1 \
    --tag-specifications \
        'ResourceType=route-table,Tags=[{Key=Name,Value=devopsacademy-rt-private}]' 

{
    "RouteTable": {
        "Associations": [],
        "PropagatingVgws": [],
        "RouteTableId": "rtb-0af6796a6299f9ebf",
        "Routes": [
            {
                "DestinationCidrBlock": "10.0.0.0/16",
                "GatewayId": "local",
                "Origin": "CreateRouteTable",
                "State": "active"
            }
        ],
        "Tags": [
            {
                "Key": "Name",
                "Value": "devopsacademy-rt-private"
            }
        ],
        "VpcId": "vpc-0720661c365cb82b1",
        "OwnerId": "985318289922"
    }
}

```

- Commands for associating the route tables with subnets:
```
aws ec2 associate-route-table \
    --route-table-id rtb-097cac5fa2f7c02cb \
    --subnet-id subnet-039e2737426c5c8c1

aws ec2 associate-route-table \
    --route-table-id rtb-097cac5fa2f7c02cb \
    --subnet-id subnet-004169e31a0253465

aws ec2 associate-route-table \
    --route-table-id rtb-097cac5fa2f7c02cb \
    --subnet-id subnet-0bf9ddd3baf60d118
```
```
aws ec2 associate-route-table \
    --route-table-id rtb-0af6796a6299f9ebf \
    --subnet-id subnet-0e9340f9f478ed095

aws ec2 associate-route-table \
    --route-table-id rtb-0af6796a6299f9ebf \
    --subnet-id subnet-061e60329a5f4a688

aws ec2 associate-route-table \
    --route-table-id rtb-0af6796a6299f9ebf \
    --subnet-id subnet-0c7203e6a0860e521
```

- Commands for creating the following routes:

|route table|destination|target|
|-|-|-|
|devopsacademy-rt-public|0.0.0.0|`devopsacademy-igw`|
|devopsacademy-rt-private|0.0.0.0|`devopsacademy-ngw`|

```
aws ec2 create-route \
    --route-table-id rtb-097cac5fa2f7c02cb \
    --destination-cidr-block 0.0.0.0/0 \
    --gateway-id igw-02b6bf5ddbb751858
```

```
aws ec2 create-route \
    --route-table-id rtb-097cac5fa2f7c02cb \
    --destination-cidr-block 0.0.0.0/0 \
    --nat-gateway-id nat-05dcc5d7e2c153450
```

- Answer the following questions:
  - Why did you add 0.0.0.0 route to the IGW on public route table?
    ```
    0.0.0.0/0, represents all IPv4 addresses.
    ```

  - Why did you add 0.0.0.0 route to the NGW on private route table?
    ```
    0.0.0.0/0, represents all IPv4 addresses.
    ```
    
  - What is the difference of IGW and NGW?
    ```
     An internet gateway (IGW) is a horizontally scaled, redundant, and highly available VPC component that allows communication between your VPC and the internet.

     You can use a network address translation (NAT) gateway (NGW) to enable instances in a private subnet to connect to the internet or other AWS services, **but prevent the internet from initiating a connection with those instances**.
    ```
    
  - Can you delete the destination route to your VPC network? Why?
    ```
     You cannot delete the “local” route from your route table.
     
     If you've associated an IPv6 CIDR block with your VPC, your route tables contain a local route for the IPv6 CIDR block. You cannot modify or delete these routes in a subnet route table or in the main route table.
    ```
    
  - What happens if you do not associate your route table with any subnets?
    ```
    Subnets that aren't explicitly associated with any route table have an implicit association with the main route table.
    ```


- Any extra challenges faced?


<!-- Don't change anything below this point-->
***
Answer for exercise [c02-network07](https://github.com/devopsacademyau/academy/blob/477b00517edd51ed2e46038ec310d324a0d3f252/classes/02class/exercises/c02-network07/README.md)