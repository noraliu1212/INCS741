# INCS741 Group Assignment: Implementation of Rail Fence Cipher 
# README.md file Group Memembers: Nora Liu, Parker Cheng, Yejun Wang
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
5. install from the Docker repo
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

## Step 2 Implementation of Application using Python Code app.py and docker file
We have been written our own implementation of Rail Fence Cipher application using python code and Docker file provided by Instructor and we have been uploaded python code and docker file on a website for easier access. Anyone wish to access to all file could also download them from Canvas through the INCS 741 Group Assignment Submission Part. 

For quick access, you could also download them from `http://34.28.177.100:3333/` The necessary files are under data directory

<img width="458" alt="Screenshot 2023-10-09 162358" src="https://github.com/Parkerpupppp/741-readme/assets/123425669/fcb20913-5bc7-4884-98df-ce62d61ee8ab">

## Step 3 Build Docker Images

We need to build docker images using our docker file.

First, we should go to the directory where we have our docker file.

Use `cd` command to change the directory to the required dir

<img width="161" alt="Screenshot 2023-10-09 172212" src="https://github.com/Parkerpupppp/741-readme/assets/123425669/ec269c4c-749a-4f0e-9a11-ce1ac53071a7">

Use the next command to build the docker image
```
sudo docker build --tag rf-docker
``` 
You could use command to check if you have the docker image ready
```
sudo docker images
```
You will see something like this

<img width="372" alt="Screenshot 2023-10-09 172716" src="https://github.com/Parkerpupppp/741-readme/assets/123425669/11ddb33d-8cbb-40c7-a8df-600dae3759f1">

## Step 4 Run a Docker Container
Once the image is built, you can run a Docker container from it using the docker run command(Linux):
```
sudo docker run -p 5000:5000 rf-docker 
```
`sudo` indicates running Docker as the superuser, `docker run` command to create and run a Docker container. `-p 5000:5000` specifies port mapping, this part of command tells Docker to map port 5000 on your host machine to port 5000 in the Docker container. This allowing external access to the Rail Fence Cipher application running inside the container. `rf-docker` is the Docker image that was created before. 

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
#### Note: Before performing encryption or decryption, ensure that all input boxes are cleared.
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

### Step 6(Optional) Cleanup
If you want to stop the Docker container, you could use `Ctrl + c` to stop.
If you want to remove the Docker image, you could use the `docker rmi` command:
```
sudo docker rmi rf-docker
```
Those commands allows you to manage Docker containers for your application using a Docker file. 
