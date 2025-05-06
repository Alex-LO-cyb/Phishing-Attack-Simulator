# Phishing Attack Simulator with Gophish

For a while now, phishing has been a common and effective way for attackers to gain access to sensitive information such as login credentials, financial records, and personal data. Anti-phishing technology solutions have gotten better over time, but phishing is a constant cat-and-mouse game between the attackers and defenders. And, as is the case with most aspects of enterprise security, humans tend to be the weakest link in the defence.

![image](https://github.com/user-attachments/assets/45e4933b-7950-4970-9fa5-df30982c2f48)

## Objective

This project involves deploying and configuring a phishing attack simulation environment using Gophish, an open-source framework for simulating targeted phishing attacks via email. The goal is to raise awareness about phishing threats by exposing users to realistic simulations. By launching phishing campaigns, I will be able to analyze user behavior and improve the security culture within the organization.

## Skills learned
- Ability to plan and manage a security awareness project from deployment to analysis.
- Hands-on experience with configuring and running phishing simulations.
- Improved understanding of social engineering tactics and user behavior.
- Familiarity with mail delivery mechanisms and SMTP configuration for phishing delivery.
- Proficiency in analyzing campaign metrics and drawing actionable insights.
- Awareness of compliance and data privacy considerations in simulated attacks.

## Tools
<div>

<img src="https://img.shields.io/badge/Gophish-Phishing_Framework-005f87?style=for-the-badge&logo=gnometerminal&logoColor=white" />
<img src="https://img.shields.io/badge/Docker-Container_Tech-2496ED?style=for-the-badge&logo=docker&logoColor=white" />
<img src="https://img.shields.io/badge/Railway-Cloud_Deployment-0B0D0E?style=for-the-badge&logo=railway&logoColor=white" />
<img src="https://img.shields.io/badge/SMTP-Mail_Server_Config-EA4335?style=for-the-badge&logo=gmail&logoColor=white" />
<img src="https://img.shields.io/badge/Gophish_Dashboard-Campaign_Tracking-F4B400?style=for-the-badge&logo=googleanalytics&logoColor=white" />

</div>

##Steps

## Install & Start Gophish 
1 - Go to Github and connect > fork <a href="https://github.com/gophish/gophish">Gophish</a>

2 - Go to <a href="https://railway.app/">Railway App</a> > Sign in with GitHub > Accept the Terms

3 - You will land on this page 

<p align="center">
  <img src="https://github.com/user-attachments/assets/5ddcff68-1c1f-40b2-b984-f959af3390d4" alt="Creating a New Project on Railway from a Forked GitHub Repository" />
</p>
<p align="center"><b>Figure 1 : Creating a New Project on Railway from a Forked GitHub Repository</b></p>

4 - Next choose Deploy from GitHub repo > Configure GitHub app > Choose only selected repositories and Select the gophish repo > Install & Authorize

<p align="center">
  <img src="https://github.com/user-attachments/assets/71c38b01-796d-4c87-b8e2-e47ef79e69ab" alt="Authorizing and Selecting the Gophish Repository for Deployment" />
</p>
<p align="center"><b>Figure 2 : Creating a New Project on Railway from a Forked GitHub Repository</b></p>
    
5 - Click on your gophish's project > Settings > Generate Domain and select port 3333

## ![image](https://github.com/user-attachments/assets/08242aaf-29de-4393-b897-20d6b22e4f39) 
## Ref3 : Generating a Public Domain for the Gophish Instance

6 - Next, in the Variables tab, create a new variable PORT with the value 3333

## ![image](https://github.com/user-attachments/assets/46c46f57-681f-49f9-8d60-560a5a0ee3bb)
## Ref4 : Setting the PORT Environment Variable in Railway

7 - Under Deployments, click View Logs for the latest deployment, and find an entry similar to Please login with the username admin and the password

## ![image](https://github.com/user-attachments/assets/6b318532-a111-46e3-adc7-3036a885bf40)
## Ref5 : Retrieving Gophish Admin Credentials from Deployment Logs

8 - Finally, edit the config.json file in your forked Gophish repository, and make the following changes:

Change the value of listen_url from 127.0.0.1:3333 to 0.0.0.0:3333 (this will make the service listen on the public address).
Change the value of use_tls from true to false (Railway will automatically create and maintain the TLS endpoint).
Add the Railway domain in trusted_origins e.g. "xxx.up.railway.app" (use your custom domain instead if you have configured it).

## ![image](https://github.com/user-attachments/assets/6996abdd-f0ff-4b19-b52a-c72d8a6e4345)

9 - Once you commit your changes, Railway will trigger the deployment again. If all goes well, you'll see the following when you launch the deployment URL.

## ![image](https://github.com/user-attachments/assets/06cc86ab-3482-4d6b-bd52-7bb24792a898)


## Run Phishing Attack Simulations with Gophish
1 - Login to the Gophish admin server using the temporary credentials found in the deployment logs, and change the password upon login.
- username = admin 
- password = #can be found in the deploy log

2 - Now that you have a functional setup, play around with the various settings to generate realistic (in your context) phishing templates. In the minimum, you'll need to configure:

- Users & groups to send the simulated phishing emails
- Phishing email templates, including attachments (see supported)
- Sending profiles to specify sending SMTP relay details
- Landing pages returned to users when they click the phishing links

3 - Once you have configured the above settings, it's time to create and launch a campaign. Navigate to the Campaigns page and click New Campaign. Most of the fields are self-explanatory and use the templates configured earlier, the URL is the domain of the Gophish listener.

4 - Click Launch Campaign to trigger the campaign.

##![image](https://github.com/user-attachments/assets/5459923c-2bae-4e2e-83bd-2bab21f2428d)
## Ref6 : Accessing the Gophish Dashboard After Successful Deployment
