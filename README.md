# Maven

This is a hands-on tutorial, on how to launch and configure an EC2 instance, install Apache to serve web content, and set up Maven for managing Java-based projects. This will guide you through every step, from choosing the appropriate EC2 instance type to configuring security groups and ensuring your installations run smoothly. By the end of this course, you'll be equipped to host websites and manage Java dependencies on a scalable cloud environment. 

<h2>Create and Launch an EC2 instance on AWS</h2>
<li>Create or Sign into AWS</li>
<li>name the instance and select the Ubuntu image</li>

![mvn](https://github.com/user-attachments/assets/5b02b28b-53b8-4598-b1f1-4171ca5d8ffb)

<li>use the t2.micro default</li>
<li>create a keypair</li>

![mvn key](https://github.com/user-attachments/assets/0dba0a1a-1ad7-4b91-9d6b-86df94a8234e)

<li>accept the remaining default settings and launch the instance</li>

![mvn instance](https://github.com/user-attachments/assets/34ed988d-7e50-4ea1-a575-b628e3334e1a)

<li>SSH into the instance from Git bash. Copy the public IP of the instance and paste in bash using the following command: ssh -i Downloads/buildkey.pem ubuntu@'ip address'</li>

![mvn ssh](https://github.com/user-attachments/assets/88b02492-9d6c-4cd7-b650-6dc361295b6a)

<li>Now run the command: sudo apt update. Its primary purpose is to update the package lists for repositories and ensure your system has the latest information about the available software and updates.</li>

![sudo update](https://github.com/user-attachments/assets/8f259014-3f8a-4ae9-9a43-dde78c5bac96)

<li>git is preinstalled on the ubuntu image</li>

![mvn git](https://github.com/user-attachments/assets/ad5fce1c-5ec3-4fcc-a78e-179ace8e8279)

<li>install the jdk maven dependency: sudo apt search jdk (openjdk-11-jdk). the version will depend on the project. We will be using jdk-11. enter in git: sudo apt install openjdk-11-jdk -y. then java -version to see its latest version</li>

![jdk11](https://github.com/user-attachments/assets/1da8119b-52fd-44f4-bd3c-698e0c1c686d)

![version](https://github.com/user-attachments/assets/5817c09b-2c05-478a-bbff-43264f09c639)

<li>We will now install Maven: sudo apt install maven -y, followed by mvn -version</li>

![mvn version](https://github.com/user-attachments/assets/771bf2ee-9ea2-4219-8b83-fe306a7f7c14)

<li>status shows errors due to no pom file: mvn status</li>

![no pom error](https://github.com/user-attachments/assets/ca7dbb3c-1b34-4e9b-952d-f8e068edbfe8)

<li>Now clone the source code: git clone https://github.com/hkhcoder/vprofile-project.git</li>

![project](https://github.com/user-attachments/assets/3b132b14-7265-40f6-8de6-251d086f58e2)

<li>change into the vprofile-project directory to see the pom file</li>

![pom file](https://github.com/user-attachments/assets/2e057b53-ade2-4e18-bfe7-bfad98a926fe)

<li>We now validate Maven: mvn validate, and run mvn test. Maven will download the dependencies to run the test</li>

![mvn validate](https://github.com/user-attachments/assets/8b5b4444-b026-4916-9a62-cf969150ba91)

![mvn test](https://github.com/user-attachments/assets/c89ff291-82d9-4069-8839-48e56ed6da38)


