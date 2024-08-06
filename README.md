<br>

<h1 align="center">Stage III - Working Incidents & Incident Response</h1>

<br>

<br>

In this lab we're gong to **Investigate and Work the Incidents** being generated within **Microsoft Sentinel**.

We'll do this in accordance with the [**NIST 800-61**](https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-61r2.pdf) **Incident Management Lifecycle**.

<br>

<p align="center">
<img width="900" src="https://github.com/user-attachments/assets/c72ba407-5700-4f04-912a-3cb76e8c46dc" alt="Banner"/>
<br />
<br />


<details close> 
<summary> <h2>4 Step Incident Response Guidance / Guidelines</h2> </summary>
<br>

## Step ➀ ➜ Preparation

We've completed this step already by:

- Setting Up **Logging** for all of our Resources.

- **Ingesting all of the Logs** into the **Log Analytics Workspace**.

- Configuring **Microsoft Sentinel** & **Alert Rules**.

<br>

<br>

## Step ➁ ➜ Detection & Analysis

<br>

>   <details close> 
>   
> **<summary> 📝 Explanation</summary>**
> 
> This phase gets kicked off when someone notices some kind of **Anomaly in the System**.
> 
> In our case we configured a bunch of Alerts ➜ and the fact that an **Incident was Created** ➜ is the beggining of our **Detection Phase**.
> 
>   </details>

<br>

**1️⃣** Set the **Severity**, the **Status** & the **Owner** of the Incident.

**2️⃣** **View Full Details**

**3️⃣** Observe the **Activity Log** (for the History of the Incident)

**4️⃣** Observe the **Entities** & **Incident Timeline**

**5️⃣** **Investigate** the Incident and continue trying to Determine the Scope

**6️⃣** **Inspect the Entities** and see if there are any Related Events

**7️⃣** **Determine Legitimacy** of the Incident

**8️⃣** If **True Positive** ➜ Continue | If **False Positive** ➜ Close it out

<br>

<br>

## Step ➂ ➜ Containment, Eradication & Recovery

Use this simple [**Incident Response PlayBook**](https://docs.google.com/document/d/1EQ5MzN95POLaRIMulYg3PIH3UGHtDNcGdkFvgOXyEXQ/edit#heading=h.uyxi3urvol4g) to **Remediate the Incident**.

<br>

<br>

## Step ➃ ➜ Post-Incident Activity

- Document Findings

- Close out the Incident in Sentinel

<br>

  </details>

<h2></h2>

<details close> 
<summary> <h2>Incident ❶ - Brute Force SUCCESS - Windows</h2> </summary>
<br>

> This Incident gets triggered when Sentinel detects a Successful Login after Multiple Failed Attempts.
> 
> It indicates that a Brute Force Attack was Successfully Conducted.

<br>

## Incident Description

<br>

➡️ This Incident involves observation of potential **Brute Force Attempts against a Windows VM**.

<br>

![azure portal](https://github.com/user-attachments/assets/36df51b2-cdcd-42e7-ad55-d26078edda07)

<br>

<br>

## Initial Response Actions

<br>

✔ Verify the Authenticity of the Alert or Report.

✔ Immediately Isolate the Machine and Change the Password of the affected User.

✔ Identify the Origin of the Attacks and determine if they are attacking or involved with anything else.

✔ Determine How and When the attack occurred.

✔ Are the NSGs not being locked down? If so ➜ check other NSGs.

✔ Assess the Potential Impact of the Incident.

✔ What Type of Account was it? What Permissions did it have?

<br>

<br>

## Detection & Analysis

<details close> 
<summary> <h3>🎯 Step-by-Step</h3> </summary>

<br>
  
**1️⃣** Set the **Severity**, the **Status** & the **Owner** of the Incident:

<br>

![azure portal](https://github.com/user-attachments/assets/36df51b2-cdcd-42e7-ad55-d26078edda07)

<br>

<h2></h2>

<br>

**2️⃣** **View Full Details**

<br>

![azure portal](https://github.com/user-attachments/assets/36df51b2-cdcd-42e7-ad55-d26078edda07)

<br>

<h2></h2>

<br>

**3️⃣** Observe the **Activity Log**

<br>

**```Nothing to show here.```**

<br>

<h2></h2>

<br>

**4️⃣** Observe the **Entities** & **Incident Timeline**

<br>

![azure portal](https://github.com/user-attachments/assets/36df51b2-cdcd-42e7-ad55-d26078edda07)

<br>

<h2></h2>

<br>

**5️⃣** **Investigate** the Incident and continue trying to Determine the Scope

<br>

![azure portal](https://github.com/user-attachments/assets/36df51b2-cdcd-42e7-ad55-d26078edda07)

<br>

![azure portal](https://github.com/user-attachments/assets/36df51b2-cdcd-42e7-ad55-d26078edda07)

<br>

<h2></h2>

<br>

**6️⃣** **Inspect the Entities** and see if there are any Related Events

<br>

### The entity is involved with other Brute Force Attempts during the same period.

<br>

<h2></h2>

<br>

**7️⃣** **Determine Legitimacy** of the Incident

<br>

### Determined to be ➜ a **Legitimate Incident** ✅

<br>

<h2></h2>

<br>

**8️⃣** If **True Positive** ➜ Continue | If **False Positive** ➜ Close it out

<br>

### Determined to be ➜ a True Positive ✅

From the **Investigation** ➜ you can see that the **Attacker / Entity** ```63.143.47.155``` is also involved in **4 other Brute Force Attempt Instances**.

<br>

  </details>

<br>

<br>

## Containment, Eradication & Recovery

<br>

<details close> 
  
**<summary> 💡 Note</summary>**

<br>

I will address this later ➜ in the **Environment Hardening Section**.

Despite that ➜ I'm including the steps here for reference from the **Incident Response Playbook**.

<br>

  </details>

<br>

✔ **Lock down the NSG** assigned to that VM ➜ either **Entirely** or to **Only Allow Necessary Traffic**.

✔ **Reset** the affected **User’s Password**.

✔ **Enable MFA**

<br>

<br>

## Post-Incident Activity

<br>

➡️ Document Findings and Close out the Incident in Sentinel.

<br>

<details close> 
  
**<summary> 💡 Note</summary>**

<br>

Check out the **Lessons Learned Section** for more details on this Incident.

<br>

  </details>

<br>

  </details>

<h2></h2>

<details close> 
<summary> <h2>Incident ❷ - Possible Privilege Escalation - Azure Key Vault</h2> </summary>
<br>

> We're now going to **Create our Microsoft Sentinel Analytics Query Rules**.
> 
> These are going to be used to **Create Alerts** ➜ and then ultimately used to **Spin up Incidents** for certain Events taking place in our Environment.

<br>

Back in the **Azure Portal** ➜ go to **Microsoft Sentinel** ➜ and click on the **Analytics** blade

<br>

![azure portal](https://github.com/user-attachments/assets/577a0b79-d93b-466e-a365-9d1f6107a07e)

<br>

We're then going to Import all of our [Sentinel Analytics Rules](https://github.com/joshmadakor1/Cyber-Course-v2/blob/main/Sentinel-Analytics-Rules/Sentinel-Analytics-Rules(KQL%20Alert%20Queries).json).

Download the **Raw JSON File** and Save it.

<br>

![azure portal](https://github.com/user-attachments/assets/f075d305-ac55-47d5-85d0-a0e80f4b7022)

<br>

Back in **Microsoft Sentinel** ➜ click on **Import** to upload the **JSON File**.

<br>

![azure portal](https://github.com/user-attachments/assets/8085ebbc-055d-48e6-bce8-e7147d0b8ef3)

<br>

✅ We can confirm that all of our **13 Analytics Query Rules** were **Successfully Deployed**!

<br>

![azure portal](https://github.com/user-attachments/assets/26168fbd-25bd-4b1f-b5cd-23cce068badd)

<br>

  </details>

<h2></h2>

<details close> 
<summary> <h2>Incident ❸ - Brute Force SUCCESS - Microsoft Entra ID</h2> </summary>
<br>

<br>

>   <details close> 
>   
> **<summary> 📝 Explanation</summary>**
> 
> In this final stage of the lab ➜ we're going to explore some of the **Custom Analytics Rules / Alerts** that we created in **Sentinel**.
> 
> We'll look at the **Queries** that make those Events ➜ and try to go through and manually trigger at least 6 of them.
>   
> This will allow us to understand how the Analytics Rules & the KQL actually work.
> 
>   </details>

<br>

To test your alerts and incidents rule configuration ➜ simulate some attacks on the VMs and see if they show up in Sentinel (generate alerts and incidents).

⚠️ We have to make sure these work before the first observation period.

<br>

Here are some Tests to Run:

<br>

#### ❶ Trigger AAD Brute Force Success:

- Simulate brute force success against Azure AD with your attacker account (from attack-vm).

- Either use PowerShell or an incognito window to fail 10-11 consecutive logins, followed by one successful login.

<br>

<h2></h2>

<br>

#### ❷ Trigger MSSQL Brute Force Attempt:

- We'll use the ```attack-vm``` for this one.

- Use ***PowerShell*** or ***SSMS*** to simulate **Brute Force Attempt against your SQL Server** by failing 10 Consecutive Logins.

<br>

<h2></h2>

<br>

#### ❸ Trigger Malware Outbreak:

- In ```windows-vm``` generate a **Malware Alert** by using ***PowerShell*** to create 1 or more **EICAR Files**.

- 💡 You can also do this Manually by creating a Text File with an **EICAR String** in it.

<br>

<h2></h2>

<br>

#### ❹ Trigger Possible Privilege Escalation (AKV Critical Credential Retrieval or Update):

- Manually read our **Key Vault Secret** ```Tenant-Global-Admin-Password``` in the Azure portal.

<br>

<h2></h2>

<br>

#### ❺ Trigger Windows Host Firewall Tampering:

- Manually Enable & Disable the ```windows-vm``` **Firewall**.

<br>

<h2></h2>

<br>

#### ❻ Trigger Excessive Password Resets:

- Reset a **User's Password** in the Azure portal 10 times.

<br>

<h2></h2>

<br>

After each attach, wait 10-20 minutes ➜ then check Sentinel to see if you have any incidents.

<br>

>   <details close> 
>   
> **<summary> 💡 Note</summary>**
> 
> This can also help you with incident investigation later on in the lab.
> 
>   </details>

<br>

### ➡️ Incidents in Sentinel after Simulating Some Attacks:

<br>

![azure portal](https://github.com/user-attachments/assets/00cef135-106c-4f4e-a5d0-f68e2b345c14)

<br>

  </details>

<h2></h2>

<details close> 
<summary> <h2>Incident ❹ - Brute Force ATTEMPT - Linux Syslog</h2> </summary>
<br>

The following table shows the measurements taken from the insecure environment after the initial 24 hour observation period:

<br>

### Metrics - Before Securing Environment

<br>

Start Time: 1/18/2024 15:44

Stop Time: 1/19/2024 15:44

<br>

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent (Windows VM)            | 29005
| Syslog (Linux VM)                   | 16562
| SecurityAlert (Microsoft Defender for Cloud)            | 4
| SecurityIncident (Sentinel Incidents)        | 204
| NSG Inbound Malicious Flows Allowed | 2837

<br>

<h2></h2>

<br>

### Attack Maps Before Hardening / Security Controls

<br>

Before taking the screenshots ➜ the Workbooks need to be edited to only show the **last 24 hours**.

💡 The query runs over the last 30 days by default.

<br>

>   <details close> 
>   
> **<summary> 📋 Steps to Edit the Maps:</summary>**
> 
> <br>
> 
> From inside the **Workbook** ➜ click on ✏️ **Edit** 
> 
> <br>
> 
> ![azure portal](https://github.com/user-attachments/assets/8085ebbc-055d-48e6-bce8-e7147d0b8ef3)
> 
> <br>
> 
> Then go all the way down and to the right ➜ click the **↑ Edit** button
> 
> <br>
> 
> ![azure portal](https://github.com/user-attachments/assets/8085ebbc-055d-48e6-bce8-e7147d0b8ef3)
> 
> <br>
> 
> Change the **Time Range** to ```Last 24 hours```
> 
> Then press the **Run Query** button
> 
> <br>
> 
> ![azure portal](https://github.com/user-attachments/assets/8085ebbc-055d-48e6-bce8-e7147d0b8ef3)
> 
> <br>
> 
> Finally ➜ click 📒**Done Editing**
> 
> <br>
> 
> ![azure portal](https://github.com/user-attachments/assets/8085ebbc-055d-48e6-bce8-e7147d0b8ef3)
> 
> <br>
> 
> ![azure portal](https://github.com/user-attachments/assets/8085ebbc-055d-48e6-bce8-e7147d0b8ef3)
> 
> <br>
> 
>   </details>

<br>

<h2></h2>

<br>

### NSG Allowed Malicious Inbound Flows:

<br>

![azure portal](https://github.com/user-attachments/assets/8085ebbc-055d-48e6-bce8-e7147d0b8ef3)

<br>

### Linux SSH Authentication Failures:

<br>

![azure portal](https://github.com/user-attachments/assets/8085ebbc-055d-48e6-bce8-e7147d0b8ef3)

<br>

### Windows RDP/SMB Authentication Failures:

<br>

![azure portal](https://github.com/user-attachments/assets/8085ebbc-055d-48e6-bce8-e7147d0b8ef3)

<br>

### MS SQL Server Authentication Failures:

<br>

![azure portal](https://github.com/user-attachments/assets/8085ebbc-055d-48e6-bce8-e7147d0b8ef3)

<br>

  </details>

<h2></h2>

<br>

<br>

<br>

<br>

<br>

<br>

<br>
  
<br>
