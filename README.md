# VPC
   # What is virtual private cloud
   . A vpc is a virtual network that closely resembles a traditional networking that we operate on our own data centre, 
     with the benefits of using scalable infrastructure of AWS.
   . To simple say vpc is a virtual network or data center inside AWS for one client. It is logically isolated from other virtual network
     in the AWS cloud.
   . Max 5 vpc can be created inside one region and 200 subnets in 1 vpc.
   . We can allocate max 5 elastic IPs.
   # components of vpc
   1) CIDR & IP Address subnets
   2) implied router & routing table
   3) Internet gateway
   4) security group
   5) Network ACL
   6) Virtual private gateway
   7) Peering connections
   8) Elastic Ip
   # Types Of VPC
     1) Default vpc
     2) Custom vpc
  # steps to create vpc
   ``` Create vpc -> subnet -> Internet Gateway -> Route Table ```
  # Components of VPC
   1) Public Subnet: 
    . If a subnets traffic is routed to an Internet Gateway, the subnet is known as public subnet.
    . If we want to our instance in public subnet to communicate with the internet over IPv4,
      it must have IP4 adress or an Elastic IP address.
      
   2) Private Subnet: 
    . If a subnet does not have a route to the internet gateway, the subnet is known a private subnet.
  # Note: When we created a vpc, we must specify an IPv4 CIDR Block for the VPC. The allowed block size is between /16 t0 /28 and the first four & last IP Address of subnet cannot assigned ->
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
     
