<h1>AWS Lab SSH into EC2 Instance</h1>

<h2>Description</h2>
In this lab, I will deploy an ec2 (elastic compute) instance and ssh into it. I will create an admin user. I will create a vpc (virtual private cloud) with two subnets, a public and private one. An internet gateway will be attached to the vpc. The public subnet will be linked to a routing table that sends network traffic, not destined for internal resources, out to the internet via the internet gateway. I will create a security group that allows ssh connects to the ec2 instance. When I create the ec2 instance, I will place it in the public subnet and the security group so that I can access it from the internet.
</br>
</br>

<img src="https://imgur.com/M7vGzx3.png" height="80%" width="80%"/>

<h2>Multi-Factor Authentication</h2>
Once I signed up for AWS, I enabled multifactor authentication for my root account.
</br>
</br>

<img src="https://imgur.com/e1oGQBH.png" height="80%" width="80%"/>
<h2>Billing Alarm</h2>
I setup a billing alarm to warn me if I unexpectedly rack up charges. I’m using AWS’s free tier. I used the “Zero-Spend Budget” template.
</br>
</br>

<img src="https://imgur.com/BRiQ6dH.png" height="80%" width="80%"/>

<h2>Creating  Non-Root User Account</h2>
Using IAM (Identity and Access Management), I created a group called admins and assigned the AdministratorAccess permission policy to it. I added JDoe to the group. It’s best practice to add users to groups, than to assign custom permissions to each user because as the company grows it will be impossible to manage each users access permissions.
</br>
</br>

<img src="https://imgur.com/o2hVOXw.png" height="80%" width="80%"/>
<img src="https://imgur.com/tBv0VO6.png" height="80%" width="80%"/>

<h2>Creating A Virtual Private Cloud</h2>
I created a vpc called my-vpc-vpc.
</br>
</br>

<img src="https://imgur.com/TJXeMhH.png" height="80%" width="80%"/>

The internet gateway was automatically created and attached to my vpc. The internet gateway allows internet traffic to and from the vpc subnets.
</br>


<img src="https://imgur.com/qvzfIEm.png" height="80%" width="80%"/>

I created a route table and configured it to send traffic that isn’t destined for my local network to the internet gateway. I linked the routing table to my public subnet.
</br>

<img src="https://imgur.com/WUiSShH.png" height="80%" width="80%"/>


<h2>Security Group</h2>
Security groups are firewalls for each resource inside your vpc. By default, they don’t allow any inbound traffic, but they allow outbound. </br>
I created a security group to allow SSH connections by creating an inbound rule that always SSH connections from any IP. This isn’t best practice because anyone on the internet can target my instance. My laptop can't be configured to have a static IP because the internet isn’t mine. In a business setting you should set a static IP.
</br>
</br>

<img src="https://imgur.com/ntMMkuK.png" height="80%" width="80%"/>

<h2>EC2 Instance</h2>
I created an EC2 instance and created a key to SSH into it using Putty. I placed the ec2 instance in my security group that allows SSH connections and the public subnet that allows internet access through the routing table configuration.
</br>
</br>

<img src="https://imgur.com/cvKcOK2.png" height="80%" width="80%"/>


