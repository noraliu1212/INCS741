# INCS741 Group Assignment: Implementation of Rail Fence Cipher 
# README.md file Group Memembers: Nora Liu, Parker Cheng, Yejun Wang
> [!NOTE]
> The pictures attached under the README.md could be lost due to missing directory (you may not able to find the proper directory of images), in such case, please click the link to gain full access to images: https://github.com/noraliu1212/INCS741/blob/main/README.md 

## Step1 Installation Docker
Open the terminal in your Virtual Machine; we are using Ubuntu 20.04 Desktop LTS, use following command lines to install docker: 

1. Use command refreshes the list of available packages
```
sudo apt update
```

2. Install a few prerequisite packages which let apt use packages over HTTPS
```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

3. Add the GPG key for the official Docker repository to your system
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

4. Add the Docker repository to APT sources
```
sudo add-apt-repository
``` 
5. Install from the Docker repo
```
apt-cache policy docker-ce
```

6. Get the latest version of docker pakages
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

After this, you should have the latest docker packages installed. you can use following command to check the docker version.
```
sudo docker -v
```

## Step 2 Implementation of Application using Python Code app.py and Dockerfile
We have been written our own implementation of Rail Fence Cipher application using python code and Dockerfile provided by Instructor.
Anyone wish to access to all file could also download them from Canvas through the INCS 741 Group Assignment Submission Part. 

## Step 3 Build Docker Images

We need to build docker images using our Dockerfile.

First, we should go to the directory where we have our Dockerfile.

Use `cd` command to change the directory to the required directory.

Use the next command to build the Docker image
```
sudo docker build --tag rf-docker
``` 
You could use `docker images` command to check if you have the Docker image ready
```
sudo docker images
```
You will see something like this

![docker_build_screenshot](https://github.com/noraliu1212/INCS741/blob/main/docker_build.png)

## Step 4 Run a Docker Container
Once the image is built, you can run a Docker container from it using the  `docker run` command(Linux):
```
sudo docker run -p 5000:5000 rf-docker 
```
`sudo` indicates running Docker as the superuser, `docker run` command to create and run a Docker container. `-p 5000:5000` specifies port mapping, this part of command tells Docker to map port 5000 on your host machine to port 5000 in the Docker container. This allowing external access to the Rail Fence Cipher application running inside the container. `rf-docker` is the Docker image that was created before. 

You will see something like this
![docker_run_screenshot](https://github.com/noraliu1212/INCS741/blob/main/docker_run.png)

## Step 5 Access to Rail Fence Cipher Application
After the initiation of Docker Container, you can access the Rail Fence Cipher through any web browser(for example, FireFox). The application will run inside the Docker container as per Dockerfile's instruction. 
The application could be access through the link:

[Rail Fence Cipher](127.0.0.1:5000)

```
127.0.0.1:5000
```

Here `127.0.0.1` is the IP address of the Virtual Box which is configured in Ubuntu 20.04. For general access, the IP address need to be changed to your own IP address. You could obtain your own IP address using the Linux command: 
```
ifconfig
```
Here is the application interface looks like:

![Application Interface](https://github.com/noraliu1212/INCS741/blob/main/Application%20Interface.png)

### Manual of Using the Rail Fence Cipher Application

> [!NOTE]
> Before performing encryption or decryption, ensure that all input boxes are cleared.
> The Rail Fence Cipher Application is case insensetive.
> The Rail Fence Cipher Application is space sensetive, Application will treat text with space and without space differently. 

#### Encryption:
To encrypt a message using the Rail Fence Cipher:

1. Place the plaintext message in the top box.

2. Adjust the key using the Depth (D) and Repetitions (R) values, where:
* D (Depth) determines the number of rails or rows in the cipher.
* R (Repetitions) specifies how many times the algorithm should repeat itself.
3. After setting up the plaintext message and key values (D and R), click the "Encrypt/Decrypt" button.

4. The resulting ciphertext will appear in the bottom box.

#### Decryption:
To decrypt a Rail Fence Cipher message:

1. Enter the ciphertext in the bottom box.

2. Adjust the key using the Depth (D) and Repetitions (R) values, following the same principles as in encryption.

3. Once the ciphertext and key values (D and R) are set, click the "Encrypt/Decrypt" button.

4. The decrypted plaintext will be displayed in the top box.

### Example of Using Rail Fence Cipher Application
#### Encryption
To encrypt a Plain Text message: **Thisisaexampleofhowtoencryptplaintext** with D value of 2 and R value of 4, firstly place the plain text in the top box and then adjust the D and R value. After setting up the plain text message and key values (D and R), click the "Encrypt/Decrypt" button. The resulting ciphertext appears in the bottom box which is: **thnptanhotlpeciweelxrstxoaayiotfimpse**

![example_1](https://github.com/noraliu1212/INCS741/blob/main/example_1.png)


#### Decryption
To decrypt a Cipher Text message: **aeyoedpxeeaehntolicrfpwrtotthohcrtpmex** with D value of 4 and R value of 6, firstly place the cipher text in the bottom box and then adjust the D and R value. After setting up the cipher text message and key values (D and R), click the "Encrypt/Decrypt" button. The resulting plaintext appears in the top box which is: **anotherexampleofhowtodecryptciphertext**

![example_2](https://github.com/noraliu1212/INCS741/blob/main/example_2.png)


### Step 6 (Optional) Cleanup
If you want to stop the Docker container, you could use `Ctrl + c` to stop.
If you want to remove the Docker image, you could use the `docker rmi` command:
```
sudo docker rmi rf-docker
```
Those commands allows you to manage Docker containers for your application using a Dockerfile. 
