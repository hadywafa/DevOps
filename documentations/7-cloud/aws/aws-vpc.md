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

![alt text](images/each-byte-can-contain-255-possible-numbers.png)

### network devices working with binary data

![alt text](images/network-devices-working-with-binary-data.png)

### IP = Network Number + Host Number

![alt text](images/ip-form.png)

### Class full addressing (old)

![alt text](images/classfull-addressing-1.png)
![alt text](images/classfull-addressing-2.png)

### CIDR Classless Inter-Domain Routing (new)

![alt text](images/cidr-1.png)
![alt text](images/cidr-2.png)
![alt text](images/cidr-3.png)
![alt text](images/cidr-4.png)
![alt text](images/cidr-5.png)
![alt text](images/cidr-6.png)
![alt text](images/cidr-7.png)

## Design VPC subnets in AWS

![alt text](images/private-ips-from-iana.png)

![alt text](images/private-ips-considrations.png)

### We create subnets from host id not from network id

![alt text](images/subnets-from-host-id-1.png)

![alt text](images/subnets-from-host-id-2.png)

### Calculation of Subnets

![alt text](images/network-to-create-subnets-from-it.png)

- To identical subnets of **/17**
![alt text](images/calc-subnets-ex1-1.png)
![alt text](images/calc-subnets-ex1-2.png)

- To identical subnets of **/18**
![alt text](images/calc-subnets-ex2-1.png)
![alt text](images/calc-subnets-ex2-2.png)

- To mixed size subnets
 ![alt text](images/calc-subnets-ex3.png)

- CIDR address should not overlaps with existing subnet CIDR with
![alt text](images/calc-subnets-note.png)

### Reserved IPs for any subnets

![alt text](images/reserved-ips-for-any-subnets.png)

## Example Design VPC subnets in AWS
