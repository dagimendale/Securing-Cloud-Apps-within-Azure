# Setting up and Securing a Web App within Azure
In this project, I build, host, and design a web application within the Azure environment, focusing on both the deployment and security aspects.

## Project Overview
This project walks through:
- Creating a web application in Azure.
- Deploying a Docker container.
- Customizing the web app.
- Securing the web app using Azure Key Vault and SSL certificates.

By the end of this project, you will learn how to:
- Create an Azure web app.
- Deploy a Docker container.
- Secure the application using Azure Key Vault and certificates.


## Project Breakdown
### 1. Setting Up the Azure Web App
- **Create a Web App**: Navigate to **App Services** and select "+ Create."
    - Choose subscription, resource group, domain name, runtime (PHP 8.2), and OS (Linux).
    - Select **Basic B1** as the pricing plan.

**Screenshots**:


<img width="400" img height="100" alt="Screenshot 2024-06-22 150140" src="https://github.com/dagimendale/AZUREproject/assets/142032863/d5dec099-91c7-477d-a120-fbab29fdbc08">
<img width="400" img height="100" alt="Screenshot 2024-06-22 150452" src="https://github.com/dagimendale/AZUREproject/assets/142032863/9ba446b5-8d75-479e-9f2d-d49741cb9576">
<img width="400" img height="200" alt="Screenshot 2024-06-22 150656" src="https://github.com/dagimendale/AZUREproject/assets/142032863/ca1bc3fd-c249-4a97-baeb-15f8cc779397">


<img width="400" img height="200" alt="Screenshot 2024-06-22 150758" src="https://github.com/dagimendale/AZUREproject/assets/142032863/d952ae75-7e57-43af-ba83-cf74e6c1e1cb">

<img width="400" img height="200" alt="Screenshot 2024-06-22 184214" src="https://github.com/dagimendale/AZUREproject/assets/142032863/63cfc1a1-851c-481f-99cf-66fe16eed6c4">

### 2. Deploy a Container on the Web App
- Open Azure Cloud Shell and run the following command to deploy a preset [Docker container](https://hub.docker.com/r/cyberxsecurity/project1-apachewebserver), which contains the framework for the cyber blog webpage I am trying to create.:
```bash
az webapp config container set --name <app-name> --resource-group <resource-group> --docker-custom-image-name <container-name> --enable-app-service-storage -t
```
- Verify the container deployment:
```bash
az webapp config container show --name <app-name> --resource-group <resource-group>
```

**Screenshots**:



<img width="400" img height="100" alt="Screenshot 2024-07-03 114637" src="https://github.com/dagimendale/AZUREproject/assets/142032863/5ec08e7c-1470-4b5f-a709-ee6c63b22b2a"> 


<img width="400" img height="100" alt="Screenshot 2024-07-03 114826" src="https://github.com/dagimendale/AZUREproject/assets/142032863/359d365a-5c96-4d1b-b821-974a44a97bec"> 

<img width="400"  img height="100" alt="Screenshot 2024-07-03 115016" src="https://github.com/dagimendale/AZUREproject/assets/142032863/36745b82-0e56-46ac-b373-328fbb11c992">


### 3.Customizing the Web App
- SSH into the container and navigate to /var/www/html.

- Edit the index.html file with:
```bash
nano index.html
```
- Update the HTML content with your own details and blog posts.


**Screenshots**:



<img width="400" img height="100" alt="Screenshot 2024-07-03 115153" src="https://github.com/dagimendale/AZUREproject/assets/142032863/dfaa26d9-a2c3-4b19-af65-22a9327c2543">



<img width="400" img height="100" alt="Screenshot 2024-07-03 115341" src="https://github.com/dagimendale/AZUREproject/assets/142032863/eba493b8-9bf5-4269-8c29-1849dd91f5a0">


<img width="400" img height="250" alt="Screenshot 2024-08-04 182431" src="https://github.com/user-attachments/assets/747d7f66-79fd-4145-ad53-d9ce2f9a5bc2">


<img width="400" img height="250" alt="Screenshot 2024-08-04 182457" src="https://github.com/user-attachments/assets/4773db0e-f0a3-4ddd-a3b9-142f2c561c32">



<img width="500" img height="250" alt="Screenshot 2024-08-04 182407" src="https://github.com/user-attachments/assets/ec5221a6-7fa2-4a79-b85d-a4bd41041b92">


### 4. Securing the Web App
#### 4.1 Create a Key Vault
- Navigate to Key Vaults in Azure and create a new key vault.
    - Assign subscription, resource group, and select the Standard pricing tier.
    - Leave the default options for all of the other tabs (Access Policy, Networking, Tags)
- After your key vault has been created, select your new resource to view your new key vault. Preview the options available on your key vault to store secure information, including "Keys", "Secrets", & "Certificates".

**Screenshots**:


<img width="262" alt="Screenshot 2024-08-17 150740" src="https://github.com/user-attachments/assets/55455236-52aa-4c83-a3e8-6a3404c02b65">



<img width="412" alt="Screenshot 2024-08-17 151132" src="https://github.com/user-attachments/assets/ac90876b-ecca-4e2e-ab16-102af6629fdc">


#### 4.2 Create and Analyze Certificates
- Generate Certificate and Key: Use the following OpenSSL command in Azure Cloud Shell to create a self-signed certificate valid for 365 days:

```bash
openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout <privatekeyname.key> -out <certificatename.crt> -addext "extendedKeyUsage=serverAuth"
```
- Convert to PFX Format: Azure requires PFX format for certificates. Convert your certificate using this command:

```bash
openssl pkcs12 -export -out <new_certificatename.pfx> -inkey <keyname.key> -in <certificatename.crt>
```
- Download PFX Certificate:
   - In Azure Cloud Shell, click the "Upload/Download" icon.
   - Select Download and enter the certificate's name (e.g., project1_cert.pfx).

### 5. Certificate Analysis
- **Self-Signed Certificate**: Examine the certificate error by navigating to https://self-signed.badssl.com/.
  

**Trusted SSL Certificate**: Analyze the certificate of your web app domain on Azure.


## Backup and Recovery of HTML Files
- To avoid losing changes, always back up your HTML files after making updates:
  
```bash
cp /var/www/html/index.html /home
```
- To restore the file:
  
```bash
cp /home/index.html /var/www/html/
```
## Conclusion
This project demonstrates how to deploy and secure a web application using Azure services. From setting up an app service to deploying Docker containers and securing it using SSL certificates, this project covers essential steps in modern web application development and security. Overall this project gives practical experience in web hosting and application security in the cloud.

































                                    
