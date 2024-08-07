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
<summary> <h2>▶️ 4 Step Incident Response Guidance / Guidelines</h2> </summary>
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

**2️⃣** **View Full Details**.

**3️⃣** Observe the **Activity Log** (for the History of the Incident).

**4️⃣** Observe the **Entities** & **Incident Timeline**.

**5️⃣** **Investigate the Incident** and continue trying to **Determine the Scope**.

**6️⃣** **Inspect the Entities** and see if there are any **Related Events**.

**7️⃣** **Determine Legitimacy** of the Incident.

**8️⃣** If **True Positive** ➜ Continue | If **False Positive** ➜ Close it out.

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

**5️⃣** **Investigate the Incident** and continue trying to **Determine the Scope**

<br>

![azure portal](https://github.com/user-attachments/assets/36df51b2-cdcd-42e7-ad55-d26078edda07)

<br>

![azure portal](https://github.com/user-attachments/assets/36df51b2-cdcd-42e7-ad55-d26078edda07)

<br>

<h2></h2>

<br>

**6️⃣** **Inspect the Entities** and see if there are any **Related Events**

<br>

The Entity is involved with other **Brute Force Attempts** during the same period.

<br>

![azure portal](https://github.com/user-attachments/assets/36df51b2-cdcd-42e7-ad55-d26078edda07)

<br>

<br>

<h2></h2>

<br>

**7️⃣** **Determine Legitimacy** of the Incident

<br>

Determined to be ➜ a **Legitimate Incident** ✅

<br>

<h2></h2>

<br>

**8️⃣** If **True Positive** ➜ Continue | If **False Positive** ➜ Close it out

<br>

Determined to be ➜ a **True Positive** ✅

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

✅ Document Findings and Close out the Incident in Sentinel.

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

> This Incident gets triggered when Sentinel detects Unusual or Unauthorized Access to Critical Credentials in Azure Key Vault.
> 
> For example ➜ when someones unauthorized reads an important Password from our Entreprise Password Manager ➜ Azure Key Vault.

<br>

## Incident Description

<br>

➡️ This Incident involves the unexpected reading of a critical **Secret** from the organization's **Key Vault**.

<br>

<br>

## Initial Response Actions

<br>

✔ Verify the Authenticity of the Alert or Report.

✔ Identify the Secret that was read and the User or Application that read it.

✔ Determine How and When the Secret was read.

✔ Assess the Potential Impact of the Incident.

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

**5️⃣** **Investigate the Incident** and continue trying to **Determine the Scope**

<br>

![azure portal](https://github.com/user-attachments/assets/36df51b2-cdcd-42e7-ad55-d26078edda07)

<br>

![azure portal](https://github.com/user-attachments/assets/36df51b2-cdcd-42e7-ad55-d26078edda07)

<br>

<h2></h2>

<br>

**6️⃣** **Inspect the Entities** and see if there are any Related Events

<br>

![azure portal](https://github.com/user-attachments/assets/36df51b2-cdcd-42e7-ad55-d26078edda07)

<br>

<h2></h2>

<br>

**7️⃣** **Determine Legitimacy** of the Incident

<br>

Determined **NOT** to be a **Legitimate Incident** ❌

<br>

<h2></h2>

<br>

**8️⃣** If **True Positive** ➜ Continue | If **False Positive** ➜ Close it out

<br>

Determined to be ➜ a **False Positive** ❌

<br>

  </details>

<br>

<br>

## Containment, Eradication & Recovery

<br>

➡️ None.

This was me viewing Key Vault Secrets at work ➜ I'm authorized to do this.

I don't think there is anything wrong with the Rule Logic here ➜ just happened to be a legitimate and authorized Incident-Generating Event.

<br>

<br>

## Post-Incident Activity

<br>

✅ Document Findings and Close out the Incident in Sentinel.

<br>

![azure portal](https://github.com/user-attachments/assets/36df51b2-cdcd-42e7-ad55-d26078edda07)

<br>

<br>

  </details>

<h2></h2>

<details close> 
<summary> <h2>Incident ❸ - Brute Force SUCCESS - Microsoft Entra ID</h2> </summary>
<br>


> The Incident gets triggered when Sentinel detects a Successful Login to a Microsoft Entra ID Account following numerous Failed Login Attempts.
> 
> For example ➜ an Attacker Successfully Accessed a Microsoft Entra ID Account by repeatedly Guessing Passwords.

<br>

## Incident Description

<br>

➡️ This Incident involves Observation of potential **Brute Force Success against Microsoft Entra ID**.

<br>

<br>

## Initial Response Actions

<br>

✔ Verify the Authenticity of the Alert or Report.

✔ Immediately Identify and Revoke Sessions/Access for Affected User.

✔ Identify the Origin of the Attacker & Determine if they are Attacking or Involved with anything else.

✔ Assess the Potential Impact of the Incident.

✔ What Type of Account was it?

✔ What Roles did it have?

✔ How long has it been since the Breach went Unattended?

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

**5️⃣** **Investigate the Incident** and continue trying to **Determine the Scope**

<br>

![azure portal](https://github.com/user-attachments/assets/36df51b2-cdcd-42e7-ad55-d26078edda07)

<br>

<h2></h2>

<br>

**6️⃣** **Inspect the Entities** and see if there are any Related Events

<br>

![azure portal](https://github.com/user-attachments/assets/36df51b2-cdcd-42e7-ad55-d26078edda07)

<br>

<h2></h2>

<br>

**7️⃣** **Determine Legitimacy** of the Incident

<br>

Determined **NOT** to be a **Legitimate Incident** ❌

<br>

<h2></h2>

<br>

**8️⃣** If **True Positive** ➜ Continue | If **False Positive** ➜ Close it out

<br>

Determined to be ➜ a **False Positive** ❌

<br>

  </details>

<br>

<br>

## Containment, Eradication & Recovery

<br>

➡️ None.

This was me viewing Key Vault Secrets at work ➜ I'm authorized to do this.

I don't think there is anything wrong with the Rule Logic here ➜ just happened to be a legitimate and authorized Incident-Generating Event.

<br>

<br>

## Post-Incident Activity

<br>

✅ Document Findings and Close out the Incident in Sentinel.

<br>

![azure portal](https://github.com/user-attachments/assets/36df51b2-cdcd-42e7-ad55-d26078edda07)

<br>

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
