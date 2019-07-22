# creation of VPC (Virtual Private Cloud)

**Use of VPC ?**
  
* Amazon Virtual Private Cloud (VPC) is a commercial cloud computing service that provides users a virtual private cloud, by "provisioning a logically isolated section of Amazon Web Services Cloud

* To know more about aws vpc follow the link https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html
    
### Prerequisites
1. Should carry the Amazon Web services Account Credentails(if not then create the AWS account)
2. Login into Amazon Dashboard by providing credentails

### Procedure to setup VPC and attach to instance
1.Create vpc and enable DNS hostname
```sh 
  # To do this step 1 follow the steps
 a. Click on "Services" present on top corner of Dashboard
 b.Scroll down and search for the Networking & Content Delivery categoery
 c.Then find the "VPC" option and click on it
 d.The page will redirect to VPC page here in the left menu click on "Your VPCs" in left side menu
 e.Then click on Create "VPC" button 
 f.Give the NAME Tag: Devoops
 g.IPv4 CIDR block : 10.1.0.0/16 and click on "create" button
 h.Then the page will referesh and you can find the Devoops VPC tag name.Click only the Devoops vpc then you find blue colour check box 
 i. Go to the Action> edit DNS Hiostbnames> Tick the check box on enable option and press save button
 ```
 
2.Creating routing table
 ```sh 
  # To do this step 2 follow the steps
 a. Click on "routing table" present on left side of Dashboard
 b.Then click on "create route table" button
 c.Then give the name tag:RT-dev
 d.Then give the vpc: here please select the latest vpc created i.e Devoops
 e.Then click on "create" button
 f.Then we should make created route table as the main routing so to make this select the latest created route table
 g.Then click on Actions > set Main Route Table 
 ```
 
 3.Create subnets and enable auto assign IP address
  ```sh 
   # To do this step 3 follow the steps
    a.Click on "subnets" present on left side of Dashboard
    b.Click on the "create subnets" button
    c.Give the name tag: Sub-Dev
    d.Select the "VPC" option with Devoops
    e.Then select the availability zone shown in the dropdown options(AS per Requirement)
    f.IPv4 CIDR bloc: 10.1.1.0/24  
    g.Then click on the create option 
    h.To make Auto assign ip select the created subnet and click on Action > Modify auto Assign-ip 
   ``` 
  4.Create internet gateway and attach to vpc 
   ```sh 
    # To do this step 4 follow the steps
    a.Click on "Internet Gate way" present on left side of Dashboard  
    b.Click on the "create Internet Gate Way" button
    c.Give the name tag: IGW-Dev
    d.Click on the "create" button
    e.After creation of internet gate way then you need to change from dattach mode to attach mode to do this
    f.select the created gate way and go to Actions > Attach to vpc > select the Devoops VPC > Attach buttton
    h.Then go to Routing Table dash board and in the bottom of page you will find subnet option and click on this subnet
    i.Then add the created subnet and click on save option
    j.Then go to Routing Table Dash board and in the bottom of page you will find routes option and click on this routes
    k.Then click on edit routes and give 0.0.0.0 and select target with internet gateway and click on save routes
  ```  
   5.Create security group and attach to VPC
   ```sh 
    # To do this step 5 follow the steps
    a.Click on "Security Group" present on left side of Dashboard  
    b.Click on the "Security Group" button
    c.Give Security name: SG-Dev
    d.Give Description: SG-Dev
    e.Select VPC: Devoops from dropdown and click on "Create" button
    Note: Here in security group dashboard at bottom of page, we need to edit the inbound option.Then only we can able to coonect to     server
    To make the changes click on inbound option and click on edit button
    select Type: Custom-tcp
    select protocol: TCP
    select Port range: 22 
    select source: Anywhere, Custom, Myip (select any one depend up on the requirement)
    select Description: Any
   ```
   
  6.Then after following all the steps we need to create instance or server
 
   
   
