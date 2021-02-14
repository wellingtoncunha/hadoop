# Creating an AWS EC2 instance AIM image

1. Go to www.aws.amazon.com and click ***Sign In to the Console***:<p>
![image001](https://user-images.githubusercontent.com/7594950/107854721-e1533180-6deb-11eb-9f01-7d4ba36d8460.png)

2. Once logged in, type ***EC2*** on the search bar and then select the ***EC2*** service from the list:<p>
![image002](https://user-images.githubusercontent.com/7594950/107884694-6dd12300-6ec4-11eb-8186-2119fff76b49.png)

3. On the right panel of ***EC2 console***, search for ***Instances*** under ***Instances*** section:<p>
![image007](https://user-images.githubusercontent.com/7594950/107884971-a9b8b800-6ec5-11eb-84b2-66bb3ca67935.png)

4. On ***EC2 console*** locate the instance you want to create a image for:<p>
![image300](https://user-images.githubusercontent.com/7594950/107885653-8d1e7f00-6ec9-11eb-9a97-a567a168d037.png)

5. Right-click on the instance row, select ***Image and templates*** and then ***Create image*** on the menu:<p>
![image301](https://user-images.githubusercontent.com/7594950/107885684-b63f0f80-6ec9-11eb-9368-db76946df5e0.png)

6. On ***Create image*** page, give a name to your image. You can also provide a description and also up other options (I'll leave it for you to explore). I am adding a tag with Key **Name** and a generic **Value** just because I am lazy and I want to save typing in the future. Then just click on ***Create image*** button:<p>
![image302](https://user-images.githubusercontent.com/7594950/107885712-e8507180-6ec9-11eb-9ca5-f8d2cc640fc1.png)

7. You can follow the image creation process by searching for ***AMIs*** under ***Images*** section on the right panel of ***EC2 console***:<p>
![image303](https://user-images.githubusercontent.com/7594950/107885802-4da46280-6eca-11eb-8511-894a8e8ec5c5.png)

8. Image generating process has low priority under AWS, so, it can take from a couple of minutes to hours to be completed. You can even stop the source EC2 instance meanwhile:<p>
![image304](https://user-images.githubusercontent.com/7594950/107885887-b986cb00-6eca-11eb-888b-4f2495ee38a1.png)

9. Once the process is complete, it will show ***available*** on ***Status*** column:<p>
![image305](https://user-images.githubusercontent.com/7594950/107885923-fce13980-6eca-11eb-9fe1-05168f6cbfef.png)
