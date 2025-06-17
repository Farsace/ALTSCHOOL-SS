
# PROJECT TITLE

PROTOTYPE WEBPAGE DEPLOYMENT ON AWS EC2 INSTANCE.

# DESCRIPTION

This project is for my ALTSCHOOL SECOND SEMESTER EXAM.


## EC2 INSTANCE PROVISIONING

During provisioning of the EC2 Instance, I followed the below steps:
 
- I created a new default security group.
- I edited the Network settings to allow traffic from port 22 (ssh), port 443 (https), port 80 (http)
- I created a new Key-pair that I will be using to ssh into the instance from a local terminal and downloaded the key-pair into a folder on my local computer (you will be prompted to download it)




## INSTALLING DEPENDENCIES

After the provisioning of the EC2 instance, I opened up a terminal on my local computer and followed the steps below to install dependencies.

- On the terminal, I changed directory into the folder that houses my key-pair:

- I executed the below command to change permission of the key-pair to enable the file to be readable by my local owner

```bash
  chmod 400 "ALT-key.pem"
  ```

- Then, I login to EC2 instance by running the below command


```bash
ssh -i "ALT-key.pem" ubuntu@ec2-18-234-140-26.compute-1.amazonaws.com
```
- After I logged in, I proceeded to run the commands below respectively to update the EC2 instance and install (*nginx*) which is the web server I used.

```bash
sudo apt update

sudo apt upgrade

sudo apt install nginx
```

## WEBPAGE HOSTING

After installing dependencies and the web server, the next steps below details how i hosted my webpage files (HTML and CSS) into my EC2 instance.

- I copied the files (HTML and CSS) from my local computer to my EC2 instance, using the command below.

``` bash
scp -i ALT-key.pem /LANDING-PAGE/index.html /LANDING-PAGE/style.css ubuntu@ec2-18-234-140-26.compute-1.amazonaws.com:/home/ubuntu
```

- Then I moved the files from the */home/ubuntu* directory on my EC2 instance into the */var/www/html* directory still on my EC2 instance, this makes sure the webpage files are hosted on my EC2 instance.

``` bash
sudo mv index.html style.css /var/www/html
```

- I renamed the *index.nginx-debian.html* file already existing in the */var/www/html* into a backup so that the web-server can actually pick my personal *index.html* file as the landing page.

```bash
sudo mv index.nginx-debian.html bkp-index
```

- After the above steps, I reloaded the nginx service so that my changes can take effect.

```bash
sudo systemctl reload nginx
```
## SCREENSHOT

Below is the screenshot of my landing page as instructed by ALTSCHOOL AFRICA
![image](https://github.com/user-attachments/assets/b28551b1-e5f1-4896-aa4c-f3d7a8c920f1)



## PUBLIC IP ADDRESS

Kindly see the public address of my EC2 instance below.

18.234.140.26
