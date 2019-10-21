
Inorder to create an ec2 instance via aws cli we have to give programatic access to a IAM user and have to access it via the access key ID and secret access key
- aws configure
- AWS Access Key ID :
- AWS Secret Access Key :
- Default region name :
- Default output format :

## - **Creating a key pair**
```
aws ec2 create-key-pair --key-name MyKeyPair
```
## - **Creating a security group for ec2 instance**
```
aws ec2 authorize-security-group-ingress --group-id sg-05932c08cec5e5e9c --protocol tcp --port 22 --cidr 0.0.0.0/0
```

## - **Creating a rule in the security group for SSH access**
```
aws ec2 authorize-security-group-ingress --group-id sg-05932c08cec5e5e9c --protocol tcp --port 22 --cidr 0.0.0.0/0
```

## - **Creating an ec2 instance**
```
aws ec2 run-instances --image-id ami-00c03f7f7f2ec15c3 --count 1 --instance-type t2.micro --key-name MyKeyPair1 --security-groups cli-demo 
```
## - **Creating a tag for the newly created instance**
```
aws ec2 create-tags \
     --resources i-03262b96cfd5f6aa6 --tags Key=Sampleserver,Value=Sampleserver
```

## - **Creating an additional volume**
```
aws ec2 create-volume \
    --volume-type gp2 \
    --size 2 \
    --availability-zone us-east-2b
```

## - **Attaching volume to the ec2 instance**
```
aws ec2 attach-volume --volume-id vol-0ef2a89e491b4ecc1 --instance-id i-0017407cca48da93f --device /dev/sdf
```
## - **To describe an Amazon EC2 instance**
```
aws ec2 describe-instances \
    --instance-ids i-03262b96cfd5f6aa6
```
## - **To describe instances based on a tag key and value**

```
aws ec2 describe-instances \
     --filters "Name=tag-key,Values=Sampleserver"
```

## - ** To terminate an Amazon EC2 instance**

```
aws ec2 terminate-instances --instance-ids i-03262b96cfd5f6aa6
```









    
    
