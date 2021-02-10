# Multi-Cloud-Architectures
Multi-Cloud Architectures for the Enterprise.

In this project we will create an AWS to Azure VPN connection with all native services on both sides.


Benefits of AWS

For anyone who is building SaaS products or externally facing applications, Plus the Availbility. AWS has more availability zones for services like S3 and EC2 as compare to Azure. 

Benefits of Azure. 

1.The biggest thing Azure has going for it is the seamless integration with Office 365.

2.Azure Active Directory forms the backbone for identity and security in the cloud.

3.Azure functions, Logic Apps and other services integrate seamlessly with Exchange, Sharepoint, Teams or many of the tools in Azure and O365 with minimal code.

4.Azure also has more traditional services such as Virtual Machines, Networking, etc. If you’re only using a single cloud provider, then it makes sense to put everything in the one place and host your VMs here as well. Microsoft has services which enable you to join Windows servers to your domain via Azure AD and without VPNs, which is great for smaller businesses.


![image](https://user-images.githubusercontent.com/58148717/105731812-6c2fc300-5ef5-11eb-8e14-5465781daf3c.png)

prerequisite:

AWS
VPC, Subnets, Route Table, Internet Gateway, Customer Gateway, Virtual Private Gateway and Site-to-Site VPN Connection.

Azure
VNet, Subnet(s), Public IP, Local Network Gateway and Virtual Network Gateway

Azure
First, we’ll create a public IP address which will ultimately get assigned to the Virtual Network Gateway.

![image](https://user-images.githubusercontent.com/58148717/105732390-ff68f880-5ef5-11eb-9b08-a2e727aadb7d.png)


Create a Virtual Network Gateway and select the public IP we created earlier.Once it has completed, note down the Public IP Address for the next steps in AWS

![image](https://user-images.githubusercontent.com/58148717/105733428-2aa01780-5ef7-11eb-8cb0-6f6275c66f64.png)


AWS
In AWS, we’ll now create a Customer Gateway. In this case, the Customer Gateway is Azure, we’ll need to enter in the Public IP Address noted down in the last step.

![image](https://user-images.githubusercontent.com/58148717/105733751-7e126580-5ef7-11eb-8a25-e70bd53ddaba.png)


Next, we’ll create the Virtual Private Gateway, this is the gateway on Amazon’s end which will allow us to route traffic to the remote network. Once created, it also needs to be attached to the VPC

![image](https://user-images.githubusercontent.com/58148717/105733948-b2862180-5ef7-11eb-9826-68b6877a30b4.png)

![image](https://user-images.githubusercontent.com/58148717/105734057-d6496780-5ef7-11eb-995e-92c329a08405.png)

initiate the VPN connection from AWS to Azure. 

create a new Site-to-Site VPN Connection. Select our newly created gateways and then enter in the IP address range of Azure.

![image](https://user-images.githubusercontent.com/58148717/105734328-2294a780-5ef8-11eb-9e51-50acf2d239f2.png)


download the generic configuration details his contains information such as the Public IP Addresses, shared keys and local tunnel addresses

![image](https://user-images.githubusercontent.com/58148717/105734435-3cce8580-5ef8-11eb-9322-c793652d3350.png)


Back in Azure.

navigate to Virtual Network Gateway > Connection > Add connection and create local network gateway for AWS tunnel

![image](https://user-images.githubusercontent.com/58148717/105735073-e9a90280-5ef8-11eb-91b8-35be871e6a41.png)


![image](https://user-images.githubusercontent.com/58148717/105736027-f843e980-5ef9-11eb-9d13-feb00e277dde.png)


create route table entries in AWS

![image](https://user-images.githubusercontent.com/58148717/105736261-36d9a400-5efa-11eb-809f-3baca1aed9a7.png)


Make sure to allow AWS and Azure’s internal IP ranges to security groups.

Afterwards use simple ping command to test. 




















































