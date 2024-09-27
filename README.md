# Setting up and Securing a Web App within Azure
In this project, I build, host, and design a web application within the Azure environment, focusing on both the deployment and security aspects.

## Project Overview
This project walks through:

Creating a web application in Azure.
Deploying a Docker container.
Customizing the web app.
Securing the web app using Azure Key Vault and SSL certificates.

By the end of this project, you will learn how to:

Create an Azure web app.
Deploy a Docker container.
Secure the application using Azure Key Vault and certificates.


## Project Breakdown
### 1. Setting Up the Azure Web App
**Create a Web App**: Navigate to **App Services** and select "+ Create."
Choose subscription, resource group, domain name, runtime (PHP 8.2), and OS (Linux).
Select **Basic B1** as the pricing plan.

#### Screenshots:
## 2. Deploy a Container on the Web App
Open Azure Cloud Shell and run the following command to deploy a Docker container:
az webapp config container set --name <app-name> --resource-group <resource-group> --docker-custom-image-name <container-name> --enable-app-service-storage -t






































# Setting up and Securing a Web App within Azure
In this project I am building, hosting, and designing my own web application all within the Azure environment. The preliminary work of this project was just setting up my Azure account with a subscription and resource group, then afterwards further familiarizing myself with the Azure environment.By the end of this project I will have created a key vault
● (1) Created a key vault.
● (2) Created a self-signed certificate.
● (3) Analyzed a self-signed certificate
● (4) Analyzed a trusted certificate
● (5) Answered review questions.


#### **PART 1A: Creating an Azure Web app**

1.As the two following images reveal, this project begins by typing in "App Services" into the search field and then once within App Services selecting the "+ Create" option.


<img width="400" img height="100" alt="Screenshot 2024-06-22 150140" src="https://github.com/dagimendale/AZUREproject/assets/142032863/d5dec099-91c7-477d-a120-fbab29fdbc08">
<img width="400" img height="100" alt="Screenshot 2024-06-22 150452" src="https://github.com/dagimendale/AZUREproject/assets/142032863/9ba446b5-8d75-479e-9f2d-d49741cb9576">

2.Now within the "Basics" section I selected my subscription and my previously created resource group. I then created the domain name, set the publish option as "code", "PHP 8.2" for the Runtime Stack, Linux for the OS, and attached the region associated with my resource group. Afterwards, I selected the service pricing plan which I put as Basic B1 option and every other section I left as default, leading to me finally selecting the create option. The newly created resource was provided with the cutom domain name we made earlier, as well as a unique IP address.

<img width="400" img height="200" alt="Screenshot 2024-06-22 150656" src="https://github.com/dagimendale/AZUREproject/assets/142032863/ca1bc3fd-c249-4a97-baeb-15f8cc779397">


<img width="400" img height="200" alt="Screenshot 2024-06-22 150758" src="https://github.com/dagimendale/AZUREproject/assets/142032863/d952ae75-7e57-43af-ba83-cf74e6c1e1cb">

<img width="400" img height="200" alt="Screenshot 2024-06-22 184214" src="https://github.com/dagimendale/AZUREproject/assets/142032863/63cfc1a1-851c-481f-99cf-66fe16eed6c4">


#### **PART 2A: Deploy a Container on the Web App**

Now using azure cloud shell I will deploy a preset [Docker container](https://hub.docker.com/r/cyberxsecurity/project1-apachewebserver) onto my web app, in which contains the framework for the cyber blog webpage I am trying to create.

1.Firstly, I opened Azure Cloud Shell and I entered "az webapp config container set --name bobswebapp --resource-group redteamRG --docker-custom-image-name cyberxsecurity/project1-apachewebserver --enable-app-service-storage -t" into the command line. This command configures my web app with the provided container's settings.

2.To verify the container has been added correctly, I entered "az webapp config container show --name bobswebapp --resource-group redteamRG" into the command line, which shows the container for the web app. Lastly, I type in the previously created domain to confirm that the container has been successfully deployed and is ready for customization.


<img width="400" img height="100" alt="Screenshot 2024-07-03 114637" src="https://github.com/dagimendale/AZUREproject/assets/142032863/5ec08e7c-1470-4b5f-a709-ee6c63b22b2a"> 


<img width="400" img height="100" alt="Screenshot 2024-07-03 114826" src="https://github.com/dagimendale/AZUREproject/assets/142032863/359d365a-5c96-4d1b-b821-974a44a97bec"> 

<img width="400"  img height="100" alt="Screenshot 2024-07-03 115016" src="https://github.com/dagimendale/AZUREproject/assets/142032863/36745b82-0e56-46ac-b373-328fbb11c992">



#### **PART 3A: Design Your Custom Web App**

After deploying the container that contained the framework the Web App, I am now able to apply my own customizations. First I used SSH within Azure to gain access to the container containing the HTML files, then once in I changed directories to the directory where the HTML files are located by running "cd /var/www/html".

That directory contains the index.html file which makes up the webpage and to edit this with my own customizations I ran "nano index.html". Then I edited the preset name, email, Linkedin link, and introduction with my own information.

Lastly, I searched for two cybersecurity based topics or stories to base my blog posts around and then typed them out within the file.

This marks the completion of creating my very own cloud-hosted web blog through Azure, the pictures below are some visuals of the web app. In the next section I will be securing this web app. 
 
⚠Important: Backing up your HTML⚠

 ● Restarting your virtual machine will often clear out any updates to your HTML 
files. Therefore, it is important to back them up every time you make an 
update!

 ● After each update to your webpage, use the following command to backup 
your index.html file to your /home directory, which stays persistent across 
reboots.: cp /var/www/html/index.html /home 
 
 ● In case you need to restore your index.html file, run the following command: cp /home/index.html /var/www/html/
 
<img width="400" img height="100" alt="Screenshot 2024-07-03 115153" src="https://github.com/dagimendale/AZUREproject/assets/142032863/dfaa26d9-a2c3-4b19-af65-22a9327c2543">

<img width="400" img height="100" alt="Screenshot 2024-07-03 115341" src="https://github.com/dagimendale/AZUREproject/assets/142032863/eba493b8-9bf5-4269-8c29-1849dd91f5a0">

(Below are some pictures of the contents of ym fully customized web app)


<img width="400" img height="250" alt="Screenshot 2024-08-04 182431" src="https://github.com/user-attachments/assets/747d7f66-79fd-4145-ad53-d9ce2f9a5bc2">


<img width="400" img height="250" alt="Screenshot 2024-08-04 182457" src="https://github.com/user-attachments/assets/4773db0e-f0a3-4ddd-a3b9-142f2c561c32">



<img width="500" img height="250" alt="Screenshot 2024-08-04 182407" src="https://github.com/user-attachments/assets/ec5221a6-7fa2-4a79-b85d-a4bd41041b92">


## **Securing The Web App**

#### **Part 1B: Creating a Key Vault**
1. Firstly, you go within in the "key vaults" services section within Azure and select "+create" to begin creating your own key vault.
<img width="420" img height="100" alt="Screenshot 2024-08-17 145614" src="https://github.com/user-attachments/assets/067072b9-f99e-4c09-bc25-6c9440eb2c68">
<img width="420" img height="100" alt="Screenshot 2024-08-17 145823" src="https://github.com/user-attachments/assets/6d24d96f-eb0c-47f3-8716-2933eb0d5c61">

2. Within the "Create key vault" section, make the following selections:
   
   ● Subscription/Resource Group: Select the same subscription and resource groups that you selected on Day 1.
   
   ● Key Vault Name: Choose a key vault name, such as project1-KeyVault. (Note: This name must be globally unique, so you will be prompted to choose a different name if 
   the one you enter has been used before.)
   
   ● Region: Select the same region that you selected on Day 1.
   
   ● Pricing tier: Select the "Standard" tier.
   
   ● Leave the default options for all of the other tabs (Access Policy, Networking, Tags)

<img width="262" alt="Screenshot 2024-08-17 150740" src="https://github.com/user-attachments/assets/55455236-52aa-4c83-a3e8-6a3404c02b65">

3. After your key vault has been created, select your new resource to view your new key vault. Preview the options available on your key vault to store secure information, including "Keys", "Secrets", & "Certificates".

<img width="412" alt="Screenshot 2024-08-17 151132" src="https://github.com/user-attachments/assets/ac90876b-ecca-4e2e-ab16-102af6629fdc">

#### **Part 2B: Creating a Self-Signed Certificate**
1. From your Azure portal, access the same Cloud Shell that you accessed before to load the Docker container. ○ From this command line, you will now use the open source cryptography
and SSL/TLS "toolkit" OpenSSL (it is preinstalled).
■ Recall that during Cryptography week, we used OpenSSL to
generate keys and an IV to encrypt a message.
2. Next, you will use OpenSSL to generate a self-signed certificate.
○ A self-signed certificate is a certificate that has not been signed by a
certificate authority.
○ These certificates are simple to create and have no expense.
○ We will explore their advantages and disadvantages in today's review
questions.
3. From the command line, enter the following command: openssl req -x509
-sha256 -nodes -days 365 -newkey rsa:2048 -keyout <privatekeyname.key>
-out <certificatename.crt> -addext "extendedKeyUsage=serverAuth"
○ For example: openssl req -x509 -sha256 -nodes -days 365 -newkey
rsa:2048 -keyout project1_key.key -out project1_cert.crt -addext
"extendedKeyUsage=serverAuth"
○ The following image shows this step:

○ We added the following options:
■ -x509: Indicates for OpenSSL to create an SSL certificate.
■ -sha256: Uses the sha256 hashing algorithm.
■ -nodes
■ -days 365: States the certificate will be valid for one year.
■ -newkey rsa:2048: Uses a 2048-bit RSA key
■ -keyout project1_key.key: The outputted name of the private key.
■ -out project1_cert.crt: The outputted name of the certificate.
■ -addext "extendedKeyUsage=serverAuth": Indicates how a public
key can be used.
4. After pressing Enter, you will be asked several questions about your certificate.
Answer the following:
○ Country Name (2 letter code) [AU]: Enter your country.
○ State or Province Name (full name) [Some State]: Enter your state.
○ Locality Name (e.g., city) [ ]: Enter your city.
○ Organization Name (e.g., company) [Internet Widgits Pty Ltd]: Enter
"Student".
○ Organizational Unit Name (e.g., section) [ ]: Leave blank by pressing
Enter.
○ Common Name (e.g., server FQDN or YOUR name) [ ]: Enter your full
domain name, such as "bobsblog.com".
○ Email Address [ ]: Leave blank by pressing Enter.
The following image shows this step:

5. Now, view your newly created key (.key) and certificate (.crt) by running ls, as
the following image shows:


○ Note that Azure requires a PFX format for its certificates.
■ The PFX format is the server certificate and the private key
combined into a single encrypted file.

6. To create a PFX format, run the following command: openssl pkcs12 -export
-out <new_certificatename.pfx> -inkey <keyname.key> -in
<certificename.crt>
○ For example: openssl pkcs12 -export -out project1_cert.pfx -inkey
project1_key.key -in project1_cert.crt
○ We added the following options:
■ pkcs12: Indicates for OpenSSL to create a PFX certificate.
■ -export -out project1_cert.pfx: States what to name the PFX file.
■ -inkey project1_key.key: This is the current private key that you are
importing.
■ -in project1_cert.crt: This is the current certificate that you are
importing.

7. After pressing Enter, you will be prompted for a password to encrypt your PFX
key.
○ Don't forget your password, as you will be prompted for it again shortly!
○ The following image shows this step:

8. View your new PFX certificate by running ls, as the following image shows:

9. To download your new PFX certificate, complete the following five steps:
○ (1) Click the "Upload/Download" icon in the toolbar above your Cloud
Shell window.
○ (2) Select "Download."
○ (3) Enter the name of your PFX certificate in the "Download a file" window.
○ (4) Click "Download."
○ (5) Then click the “Download your certificate” button.
The following image shows these steps:

#### **Part 3B: Analyze a Self-Signed Certificate**
In this part, you will use Azure to import and analyze self-signed certificates To do so,
complete the following steps:
1. From the Azure Portal, select "Key Vaults."
○ Select the key vault that you created in Part 1.
2. From your key vault, select "Certificates" and then "+ Generate/Import," as the
following image shows:

3. On the "Create a certificate" page, select the following:
○ Method of Certificate Creation: Import
○ Certificate Name: project1PFX-cert
○ Upload Certificate File: Select your PFX certificate (it's likely in your
Downloads folder)
○ Password: Enter the password that you created in Part 2
The following image shows these steps:

4. Select "Create" to upload your certificate.
○ The following success message should appear to confirm that your PFX
certificate has been uploaded to your key vault:

5. ⚠️ Normally, after uploading a certificate, you would add it to your web
application. Since you have selected the free domain option and Azure has
already provided a certificate, you will instead analyze a mock self-signed
certificate.

6. Navigate to the following webpage: https://self-signed.badssl.com/.
● This webpage represents how your application would operate if you had
added your self-signed certificate to it.
● Did your browser return an error like the one shown in the following
image?

7. Let's examine this webpage's certificate. Click "Not secure" in the search bar if
you are in Chrome, or a similar message depending on your browser, as shown
in the following image:


○ After selecting "Not secure," select "Certificate (Invalid)" from the menu to
examine the certificate.
○ Note the reason for the error based on the message on the certificate.
This is due to the fact that the certificate was not created by a trusted
CA—it would have been created by you.

#### **Part 4B: Analyze a Trusted SSL Certificate**
In this part, you will analyze a trusted SSL certificate. An advantage of using Azure's
free domain, "azurewebsites.net," is that Microsoft provides the secure SSL certificate.
To analyze this certificate, complete the following steps:
1. Open a browser, and access the domain that you created on Day 1
(webpage@azurewebsites.net).
○ Did you encounter any errors, like you did with the self-signed certificate?
2. Click on the lock icon in the top left of your browser (the left-hand side of the
search bar) to analyze your certificate and its details.
You will answer review questions about your certificate in the next part of the activity.


