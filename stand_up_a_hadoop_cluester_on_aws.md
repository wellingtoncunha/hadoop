# Configuring a Hadoop Cluster on AWS

## Generating PEM Key on AWS
The very first step (assuming you already has an AWS account) is to generate a PEM Key file (if you do not have one yet) in order to get access to the intances you're going to use, if you do not have yet, please, check [How-to generate a PEM Key on AWS](generate_aws_pem_key.md)

## Provisioning an EC2 image with Hadoop and JAVA
In order to make it easy for configuring our cluster, we are going to provision an EC2 instance, install JAVA, Hadoop and some other commom components for any node and then generate an image that we can use in the future to provision machines alike that.

1. First, we need to create an EC2 instance. If you are not familiar with that, please, check [How-to provision an EC2 instance](provision_ec2_server.md)

2. Once the server is available, we are going now to connect (SSH) to it:
    ```bash
    ssh -i ~/Downloads/hadoop.pem ubuntu@<Public IPv4 address>
    ``` 

3. Then, inside the server, we are first update apt and install nano (yes, I like it way more than vi =) ):
    ```bash
    sudo apt-get update && sudo apt-get dist-upgrade -y

    sudo apt install nano -y
    ```

4. Now, we are going to install JAVA (version 8 is the one that is working with this version of Hadoop, so, "if it is working don't touch it!"):
    ```bash
    sudo apt-get install openjdk-8-jdk -y
    ```

5. We are going now to download Hadoop version 2.8 (again, it is working). This may take a while: 
    ```bash
    wget https://archive.apache.org/dist/hadoop/core/hadoop-2.8.1/hadoop-2.8.1.tar.gz -P ~/Downloads
    ```

6. Extract Hadoop to the folder where you want to have its the installation:
    ```bash
    sudo tar zxvf ~/Downloads/hadoop-2.8.1.tar.gz -C /usr/local
    ```

7. Just to make things neat, let's remove the tar file and rename the folder by removing the version of it:
    ```bash
    # Remove installation file
    rm ~/Downloads/hadoop-2.8.1.tar.gz 

    # Rename Hadoop directory
    sudo mv /usr/local/hadoop-2.8.1 /usr/local/hadoop
    ```

8. We now need to add the environment variables to some files in order to have them set. The reason for setting them on those differents files is that there are slightly differences on where those variables should be place, depending on the configuration of the OS. Better be safe than sorry! Here are the variables that we are going to set:
    ```bash
    # JAVA configurations
    export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
    export PATH=$PATH:$JAVA_HOME/bin

    #Hadoop Related Options
    export HADOOP_HOME=/usr/local/hadoop
    export PATH=$PATH:$HADOOP_HOME/bin
    export HADOOP_CONF_DIR=/usr/local/hadoop/etc/hadoop
    ```
    And here are the places (add the block above to the end of each file):
    * nano ~/.bashrc:
        ```bash
        nano ~/.bashrc
        ```
    * nano ~/.profile:
        ```bash
        nano ~/.profile
        ```
    * sudo nano /etc/profile:
        ```bash
        sudo nano /etc/profile
        ```
    * sudo nano /etc/bash.bashrc
        ```bash
        sudo nano /etc/bash.bashrc
        ```
    * And last but not least, let's set them for our current session:
        ```bash
        source ~/.bashrc
        ```

9. For some unknown reason, one of the scripts required to start one of the Hadoop services is not reading the JAVA_HOME variable correcly. So, let's hard-code it on the script:
    ```bash
    sudo nano $HADOOP_CONF_DIR/hadoop-env.sh
    ```

    The piece that needs to be set is at the line 25, so, just replace the placeholder ${JAVA_HOME} by the JAVA path (/usr/lib/jvm/java-8-openjdk-amd64):
    * Before:
    <img width="798" alt="image200" src="https://user-images.githubusercontent.com/7594950/107885305-737c3800-6ec7-11eb-84a0-65f77dadae67.png">
    * After:
    <img width="763" alt="image201" src="https://user-images.githubusercontent.com/7594950/107885324-8abb2580-6ec7-11eb-8c49-734aed0293f7.png">

10. So we are now good to generate an AIM image for this server and will be able to use it to stand up new Hadoop clusters. Please, check [How-to create an AWS EC2 instance AIM image](generate_EC2_image.md)


This how-to guide is an extension of [Setup 4 Node Hadoop Cluster on AWS EC2 Instances](https://medium.com/@jeevananandanne/setup-4-node-hadoop-cluster-on-aws-ec2-instances-1c1eeb4453bd) article by Jeevan Anand.
