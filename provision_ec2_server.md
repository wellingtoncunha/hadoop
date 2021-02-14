# Creating an AWS EC2 instance

1. Go to www.aws.amazon.com and click ***Sign In to the Console***:<p>
![image001](https://user-images.githubusercontent.com/7594950/107854721-e1533180-6deb-11eb-9f01-7d4ba36d8460.png)

2. Once logged in, type ***EC2*** on the search bar and then select the ***EC2*** service from the list:<p>
![image002](https://user-images.githubusercontent.com/7594950/107884694-6dd12300-6ec4-11eb-8186-2119fff76b49.png)

3. On the right panel of ***EC2 console***, search for ***Key Pairs*** under ***Network & Security*** section:<p>
![image007](https://user-images.githubusercontent.com/7594950/107884971-a9b8b800-6ec5-11eb-84b2-66bb3ca67935.png)

4. On ***EC2 console*** click on ***Launch Instances*** button:<p>
![image008](https://user-images.githubusercontent.com/7594950/107884976-b0472f80-6ec5-11eb-92fb-6c3e71b2be44.png)

5. On the search bar, type *ubuntu* and hit ***enter***. Then select the instance (we are using Ubuntu Server 18) and click on ***Select*** button close to it:<p>
![image009](https://user-images.githubusercontent.com/7594950/107884986-b9d09780-6ec5-11eb-8ac1-f3c85a34a369.png)

6. Choose the instance type (we are using the one eligible for free tier) and then click on ***Next: Configure Instance Details*** button<p>
![image010](https://user-images.githubusercontent.com/7594950/107884999-c228d280-6ec5-11eb-9410-af0af99b99bd.png)

7. You can select the number of instances with the same configuration to be privisioned at once. In our case, we are going to leave *1*. You can also leave everything else as it is (unless you want to explore some options =) ). Click on ***Next: Add Storage*** button:<p>
![image011](https://user-images.githubusercontent.com/7594950/107885007-ca810d80-6ec5-11eb-9d9c-523f7df1d565.png)

8. You can add as many disk as you want (limited by the type of instance chosen), as well the size of each one (according to the limits of the volume type). In order to keep our instance on free tier, we will add the maximum allowed to it: 30 Gb (General Purpose SSD). Click on ***Next: Add Tags***:<p>
![image012](https://user-images.githubusercontent.com/7594950/107885008-d240b200-6ec5-11eb-86fd-074912a6c26f.png)

9. Tags key-value pairs are a nice way of providing information about your resources under AWS. It also enables you to search or filter easily. For this specific case, we are just going to add ***Name*** tag with *Hadoop Template Instance* value and click ***Next: Configure Security Group***:<p>
![image013](https://user-images.githubusercontent.com/7594950/107885021-dd93dd80-6ec5-11eb-858e-3292167b19fd.png)

10. Now select the security groups. First, select the ***Select an existing security group*** radio button<p>
![image014](https://user-images.githubusercontent.com/7594950/107885031-e684af00-6ec5-11eb-8c6f-13f6275904f5.png)
    **Notes**:
    * If you want to create your groups, please, check [How-to create an EC Security Group](create_ec2_security_group.md)
    * Default security group allows every IP and port inside the boundaries of the VPC 

11. You can now review all the parameters for the new instance to be provisioned. If there is anything to be change, you can go back to the specific page by clicking on the links at the top of page. if no, just click on ***Launch*** button:<p>
![image015](https://user-images.githubusercontent.com/7594950/107885043-f13f4400-6ec5-11eb-955e-3cfe31104c40.png)

12. A page will pop up asking you to select the key pair. You should also acknowledge that you are aware that without the key you won't be able to get access to the server. Then just click on ***Launch Instances***:<p>
![image016](https://user-images.githubusercontent.com/7594950/107885048-f8fee880-6ec5-11eb-98dc-132d75a6ddc9.png)

13. You can get back to the ***EC2 console*** to check the progress of your new server provisioning:<p>
![image017](https://user-images.githubusercontent.com/7594950/107885059-02885080-6ec6-11eb-97c3-68338ef71dd1.png)

14. The provisioning completion is indicated by two columns: ***Instance state***, that indicates that it is running, and the ***Status check***. If both are green, you're good. By selecting the instance, you can also get its ***Public IPv4 address*** (the one you will use to get access to it from anywhere outside the VPC) and the ***Private IPv4 addresses***, (the one to be used for communication inside the VPC boundaries):<p>
![image018](https://user-images.githubusercontent.com/7594950/107885064-09af5e80-6ec6-11eb-9079-d955b09085c2.png)