# AWS-VPC-Secure-Application




![vpc](https://github.com/yelurusrinu/AWS-VPC-Secure-Application/assets/96856227/483c4b0d-0a40-4c0e-a433-ef5e2ce9369e)





**Routing**
When you create this VPC by using the Amazon VPC console, we create a route table for the public subnets with local routes and routes to the internet gateway. We also create a route table for the private subnets with local routes, and routes to the NAT gateway, egress-only internet gateway, and gateway VPC endpoint.

**Security**

The rules that you might create for the security group that you associate with your servers. The security group must allow traffic from the load balancer over the listener port and protocol. It must also allow health check traffic.


![Example_ VPC with servers in private subnets and NAT - Amazon Virtual Private Cloud - Google Chrome 10_27_2023 5_31_13 PM](https://github.com/yelurusrinu/AWS-VPC-Secure-Application/assets/96856227/73ce3615-a2b2-45c5-b2e6-fcdf270e3f3d)


**Create the VPC**

Use the following procedure to create a VPC with a public subnet and a private subnet in two Availability Zones, and a NAT gateway in each Availability Zone.

**To create the VPC**
Open the Amazon VPC console at https://console.aws.amazon.com/vpc/.

On the dashboard, choose Create VPC.

For Resources to create, choose VPC and more.

**Configure the VPC**

For Name tag auto-generation, enter a name for the VPC.

For IPv4 CIDR block, you can keep the default suggestion, or alternatively you can enter the CIDR block required by your application or network.

If your application communicates by using IPv6 addresses, choose IPv6 CIDR block, Amazon-provided IPv6 CIDR block.

**Configure the subnets**

For Number of Availability Zones, choose 2, so that you can launch instances in multiple Availability Zones to improve resiliency.

For Number of public subnets, choose 2.

For Number of private subnets, choose 2.

You can keep the default CIDR block for the public subnet, or alternatively you can expand Customize subnet CIDR blocks and enter a CIDR block. For more information, see Subnet CIDR blocks.

For NAT gateways, choose 1 per AZ to improve resiliency.

If your application communicates by using IPv6 addresses, for Egress only internet gateway, choose Yes.

For VPC endpoints, if your instances must access an S3 bucket, keep the S3 Gateway default. Otherwise, instances in your private subnet can't access Amazon S3. There is no cost for this option, so you can keep the default if you might use an S3 bucket in the future. If you choose None, you can always add a gateway VPC endpoint later on.

For DNS options, clear Enable DNS hostnames.

Choose **Create VPC.**



**Deploy your application**

Ideally, you've finished testing your servers in a development or test environment, and created the scripts or images that you'll use to deploy your application in production.

You can use Amazon EC2 Auto Scaling to deploy servers in multiple Availability Zones and maintain the minimum server capacity required by your application.

To launch instances by using an Auto Scaling group
Create a launch template to specify the configuration information needed to launch your EC2 instances by using Amazon EC2 Auto Scaling. For step-by-step directions, see Create a launch template for your Auto Scaling group in the Amazon EC2 Auto Scaling User Guide.

Create an Auto Scaling group, which is a collection of EC2 instances with a minimum, maximum, and desired size. For step-by-step directions, see Create an Auto Scaling group using a launch template in the Amazon EC2 Auto Scaling User Guide.

Create a load balancer, which distributes traffic evenly across the instances in your Auto Scaling group, and attach the load balancer to your Auto Scaling group. For more information, see the Elastic Load Balancing User Guide and Use Elastic Load Balancing in the Amazon EC2 Auto Scaling User Guide.
