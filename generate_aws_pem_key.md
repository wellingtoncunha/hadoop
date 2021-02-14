# Generating AWS PEM Key file

One of ways AWS provides to enable access to an EC2 is with the use of a [PEM Key](https://en.wikipedia.org/wiki/Privacy-Enhanced_Mail). So, first step when configuring a fresh account is to generate a PEM file for further access to EC2 servers created under the account.

1. Go to www.aws.amazon.com and click ***Sign In to the Console***:<p>
![](https://user-images.githubusercontent.com/7594950/107854721-e1533180-6deb-11eb-9f01-7d4ba36d8460.png)

2. Once logged in, type ***EC2*** on the search bar and then select the ***EC2*** service from the list:<p>
![](https://user-images.githubusercontent.com/7594950/107884694-6dd12300-6ec4-11eb-8186-2119fff76b49.png)

3. On the right panel of ***EC2 console***, search for ***Key Pairs*** under ***Network & Security*** section:<p>
![image003](https://user-images.githubusercontent.com/7594950/107884874-34e57e00-6ec5-11eb-8c13-ba9dbafbe71f.png)


4. On the ***Key pairs*** page, click on ***Create key pair*** button:<p>
![image004](https://user-images.githubusercontent.com/7594950/107884887-43339a00-6ec5-11eb-9e55-3f20e2dbf885.png)

5. Give your PEM Key a name, select ***pem*** as file format and then click on ***Create key pair*** button:<p>
![image005](https://user-images.githubusercontent.com/7594950/107884903-4c246b80-6ec5-11eb-984f-9a01c850adf2.png)
    
    Once you click, it will download the PEM Key file to your machine:<p>
    ![image006](https://user-images.githubusercontent.com/7594950/107884913-56466a00-6ec5-11eb-8fbd-441f3e7ff461.png)

6. You won't be able to use the PEM file unless you restrict its security. In order to do so, run the following statement on the your computer terminal:<p>
    ```bash
    chmod 600 ~/Downloads/hadoop.pem 
    ```

Your PEM Key is now ready for use!