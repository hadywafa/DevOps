# Virtual Private Cloud

## Components

![alt text](images/vpc-classification.png)

- Each vpc must be in one region.
- Each vpc have multi nested subnets.
- Each subnet must be in one AZ.
- Private subnet has not public ips.
- Each subnet has range of ips.
- There is default created vpc per aws account

## Network Connections

![alt text](images/network-connection-getway.png)

## Understanding IP in AWS

![alt text](images/understanding-ip-in-aws.png)

### each byte can contain 255 possible numbers

![alt text](images/image-1.png)

### network devices working with binary data

![alt text](images/image-2.png)

### IP = Network Number + Host Number

![alt text](images/image-3.png)

### Class full addressing (old)

![alt text](images/image-4.png)
![alt text](images/image-5.png)

### CIDR Classless Inter-Domain Routing (new)

![alt text](images/image-6.png)
![alt text](images/image-7.png)
![alt text](images/image-9.png)
![alt text](images/image-11.png)
![alt text](images/image-12.png)
![alt text](images/image-13.png)
![alt text](images/image-14.png)

## Design VPC subnets in AWS

![alt text](private-ips-from-iana.png)

![alt text](private-ips-considrations.png)

### We create subnets from host id not from network id

![alt text](subnets-from-host-id-1.png)

![alt text](subnets-from-host-id-2.png)

### Calculation of Subnets

![alt text](image-5.png)

![alt text](image-6.png)

### Reserved IPs for any subnets

![alt text](reserved-ips-for-any-subnets.png)

## Example Design VPC subnets in AWS
