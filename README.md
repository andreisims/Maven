# Maven

This is a hands-on tutorial, on how to launch and configure an EC2 instance, and set up Maven for managing Java-based projects. This will guide you through every step, from choosing the appropriate EC2 instance type to configuring security groups and ensuring your installations run smoothly. By the end of this course, you'll be equipped to host websites and manage Java dependencies on a scalable cloud environment. 

<h2>Project Structure</h2>

```
vprofile-project/
├── src/
│   ├── controllers/    # Handles incoming requests
│   ├── services/       # Contains business logic
│   └── index.ts        # Application entry point
├── .env.example        # Template for environment variables
├── pom.xml             # Maven project configuration
└── README.md           # Documentation for the project
```
<h2>build process</h2>
<li>source code from developers (java, .net, C#, etc)</li>
<li>compile the code </li>
<li>test the code</li>
<li>then package the code (jar, war, exe., zip, etc)</li>

![Image](https://github.com/user-attachments/assets/18edda04-8798-4ed7-82d2-566cc6ba9ab2)
<h2>Maven Phases</h2>

![Image](https://github.com/user-attachments/assets/0faab9cc-447c-4f09-8900-46911191d885)

<li>if any phase is started, Maven will complete all of the previous steps in the phase process</li>

![Image](https://github.com/user-attachments/assets/c32c9387-5a5a-492a-97ed-91a6f5b61e1c)
<h2>Maven documentation</h2>
https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html
<h2>github repo containing files for the project</h2>
https://github.com/hkhcoder/vprofile-project

![Image](https://github.com/user-attachments/assets/7af74f0c-8ec1-4cc9-9926-44da92c7ea73)
<h2>pom.xml is the build file for Maven; the source code</h2>

![Image](https://github.com/user-attachments/assets/044dc779-25e1-4fd8-a977-b541843f25c0)
<h2>xml documentation </h2>
https://www.w3schools.com/xml/xml_whatis.asp

<h2>Create and Launch an EC2 instance on AWS</h2>
<li>Create or Sign into AWS</li>
<li>Launch Ubuntu EC2 instance in AWS to fetch the source code: name "BuildServer", Ubuntu, free tier</li>

![mvn](https://github.com/user-attachments/assets/5b02b28b-53b8-4598-b1f1-4171ca5d8ffb)

<li>Create keypair: name buildkey, .pem file, create key pairt</li>

![Image](https://github.com/user-attachments/assets/b1cf9bcb-9f9b-4250-84cd-e13a3f4d9dbc)
<li>keep defaults, launch instance</li>

![Image](https://github.com/user-attachments/assets/1372721a-ac04-4457-8eed-2b8e50946f33)

<li>SSH to instance: copy public IP, paste in git bash</li>

![Image](https://github.com/user-attachments/assets/de871031-b21d-4975-8f98-6e0520b705aa)

<li>Now run the command: sudo apt update. Its primary purpose is to update the package lists for repositories and ensure your system has the latest information about the available software and updates.</li>

![Image](https://github.com/user-attachments/assets/79afa925-a595-4178-999e-b46b37c85bc9)

<li>fetch the source code and build it with Maven. git is preinstalled on the ubuntu image</li>

![Image](https://github.com/user-attachments/assets/f8bab3ae-89ae-462a-a2cf-779a383bf9b0)
<h2>install Maven via package manager</h2>
<li>install the jdk maven dependency: sudo apt search jdk (openjdk-11-jdk). the version will depend on the project. We will be using jdk-11. 
<li>enter in git: sudo apt install openjdk-11-jdk -y</li>
<li>then java -version to see its latest version</li>

![jdk11](https://github.com/user-attachments/assets/1da8119b-52fd-44f4-bd3c-698e0c1c686d)

![version](https://github.com/user-attachments/assets/5817c09b-2c05-478a-bbff-43264f09c639)

<li>We will now install Maven: sudo apt install maven -y</li>
<li>followed by mvn -version</li>
<li>wget method if you prefer</li>
"wget https://dlcdn.apache.org/maven/maven-3/3.9.9/binaries/apache-maven-3.9.9-bin.tar.gz"
<li>and extract it: tar xzvf apache-maven-3.9.9-bin.tar.gz</li>

![Image](https://github.com/user-attachments/assets/61158afd-7c33-4ee3-9841-7fd2cb28121a)

<li>now move the Maven file, best practice. (sudo mv apache-maven-3.9.9 /opt/)</li>
https://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/opt.html
<li>check the version: mvn -version</li>

![Image](https://github.com/user-attachments/assets/c3c634ee-e29b-4317-bfe0-cd91c80ed341)

<h2>Now clone the source code</h2>
<li>git clone https://github.com/hkhcoder/vprofile-project.git</li>

![Image](https://github.com/user-attachments/assets/45ef71ea-1e7e-4912-80d4-27b4e66fc591)

![Image](https://github.com/user-attachments/assets/e204a1b8-8a50-42bd-acd9-a6c861cb504a)


<li>change into the vprofile-project directory to see the pom file</li>

![pom file](https://github.com/user-attachments/assets/2e057b53-ade2-4e18-bfe7-bfad98a926fe)

<li>We now validate Maven. This checks and identifies any possible errors in a changelog file that may cause the update goal to fail mvn validate, and run 'mvn validate'</li>

![Image](https://github.com/user-attachments/assets/dd2874df-8051-4461-93b3-8cc7ca07eac6)
<li>Maven test: Maven will execute all the phases up to and including the “test” phase. "mvn test"</li>

![mvn test](https://github.com/user-attachments/assets/c89ff291-82d9-4069-8839-48e56ed6da38)

<li>target folder contains all the final products that are the result of Maven building your project: "ls", "cd target" </li>

![Image](https://github.com/user-attachments/assets/dd401d52-021a-4f8e-867e-094aa1e9bcdb)
<li>mvn clean: removes all previously compiled files and other artifacts, ensuring that the next build starts from a clean slate</li>

![Image](https://github.com/user-attachments/assets/40c58025-d903-4afb-8e49-8f7141b9800d)
<li>mvn install and mvn clean install. "install" will not download any new files if they already exist on your system, where "clean install" removes all previous files and starts from scratch</li>

![Image](https://github.com/user-attachments/assets/ac730156-8caf-43eb-92dc-4e4aec49b056)
<li>the vprofile-v2.war is the artifact file, which is an archive of the vprofile-v2 file</li>
<li>view the dependecies</li>

![Image](https://github.com/user-attachments/assets/926ea1eb-7208-47c1-9843-02721b86471a)
<li>update pom file (vim pom.xml) from version2 (v2) to version3 (v3)</li>

![Image](https://github.com/user-attachments/assets/2906a06a-4065-4af1-9f78-d0c6f06ac074)
<li>ls target/ (shows current version) </li>

![Image](https://github.com/user-attachments/assets/37742a16-8033-464d-b5f0-0226a75e6c4a)
<li>mvn clean install shows updated version </li>

![Image](https://github.com/user-attachments/assets/71889d6e-8c4a-4de1-8b57-6a55ad5ddb58)
