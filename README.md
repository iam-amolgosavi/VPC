# VPC
   ## What is virtual private cloud
   
   . A vpc is a virtual network that closely resembles a traditional networking that we operate on our own data centre, 
     with the benefits of using scalable infrastructure of AWS.
     
   . To simple say vpc is a virtual network or data center inside AWS for one client. It is logically isolated from other virtual network
     in the AWS cloud.
     
   . Max 5 vpc can be created inside one region and 200 subnets in 1 vpc.
   
   . We can allocate max 5 elastic IPs.
   ## components of vpc
   
   1) CIDR & IP Address subnets
   2) implied router & routing table
   3) Internet gateway
   4) security group
   5) Network ACL
   6) Virtual private gateway
   7) Peering connections
   8) Elastic Ip
      
   ## Types Of VPC
     1) Default vpc
     2) Custom vpc
  ## steps to create vpc
   ``` Create vpc -> subnet -> Internet Gateway -> Route Table ```
  ## Components of VPC
  
   1) Public Subnet:
      
    . If a subnets traffic is routed to an Internet Gateway, the subnet is known as public subnet.
    
    . If we want to our instance in public subnet to communicate with the internet over IPv4,
      it must have IP4 adress or an Elastic IP address.
   
      
   2) Private Subnet:
      
    . If a subnet does not have a route to the internet gateway, the subnet is known a private subnet.
      
  #### Note: When we created a vpc, we must specify an IPv4 CIDR Block for the VPC. The allowed block size is between /16 t0 /28 and the first four & last IP Address of subnet cannot assigned ->
  #    E.g 10.0.0.0/24 address following are reserved as follows:
  #       . 10.0.0.0 --> Network Address
  #       . 10.0.0.1 --> Reserved by AWS for the VPC Router.
  #       . 10.0.0.2 --> Reserved by AWS, The IP Address of DNS server.
  #       . 10.0.0.3 --> Reserved for future use.
  #       . 10.0.0.255 --> Broadcast Address.  Aws does not support broadcast in vpc, but reserves the address.
   3) Implied Router & Route Table: 
     . It is the central routing function. It connects the different AZ together and connects the pc to the internet gateway.
      
     . We can have upto 200 route tables per pc.
     
     . Each subnet must be associated with only one route table at any given time.
     
     . If we do not specify a subnet to route table association, the subnet will be associated with default vpc route table.
     
     . we can also edit the main route table if we need, but we cannot delete the main route table.
     
     . we can associate multiple subnets with the same route table.
      
  4) Internet Gateway:
     . An IGW is a virtual router that connects a VPC to internet.
     
     . Default pc is already attached with IGW.
     
     . If we create new vpc then we must attach IGW in order to access the internet.
     
     . Ensure that our subnet's route table points to the internet gateway.
     
     . It supports both ipv4 and ipv6.
     
  5) NAT Gateway:
     . We can use a Network Address translation gateway to enable instances in a private subnet
     
      to connect to the internet or other AWS services, but prevent the internet from initiating a connection with
      those instances.
     
     . We are charged for creating and using gateway in our account. NAT gateway hourly usage and data purchase rates apply.
       Amazon ec2 charges for data transfer also apply.
     
     . To create a NAT Gateway, we must specify the public subnet in which NAT gateway reside.
     
     . No need to assign public IPs to our private instances
     
     . After we have created a NAT gateway we must update the route table associated with one or more of our private
       subnets to point internet bound traffic to the gateway.
     
     . This enables instances in your private subnets to communicate with the internet.
     
     . Deleting a NAT Gateway, disassociates its Elastic IP address, but does not releases the address from your account.

6) Security Group:
   . It is a virtual firewall works at ENI (Elastic Network Interface) level.
   
   . Upto 5 Security groups per EC2 instances interfaces can be applied.
   
   . Can only have permit rules, cannot have deny rule.

7) Network ACL:
    . It is a function performed on the implied router.
    
    . NACL is an optional layer of security layer of security for our vpc that acts as a firewall for controlling
      traffic in and out of one or more subnets.
    
    . We can create a custom NACL and associate it with a subnet.

# Difference Between Security Groups & NACL
. Security group operate at instance level and NACL operate at subnet level.

. SG support allows rules only and NACL permits allow as well as deny rules.

. SG is stateful. return traffic is automatically allowed and NACL is stateless, return traffic must be explicitly
  allowed by rules.
  
. SG applies to an instance only and NACL applies to all instances in this subnet.












   
   













     
     
