# ☁️ Unity Cloud Services Setup & Guide

**Author:** Daniel Onyejiekwe  
**Date:** June 2025

This document provides a comprehensive overview and setup guide for Unity Cloud Services, including testing insights, troubleshooting, and best practices. It's written to help Unity developers streamline their workflow using Unity’s integrated cloud tools.

---

## 📌 Table of Contents

- [Overview](#overview)
- [Core Services Explained](#core-services-explained)
- [Setup Instructions](#setup-instructions)
- [Enable Version Control (Step 5)](#-enable-version-control-step-5)
- [Best Practices](#-best-practices)
- [Troubleshooting](#-troubleshooting)
- [Screenshots](#-screenshots)
- [Conclusion](#-conclusion)

---

## 🧠 Overview

Unity Cloud Services offer cloud-based tools to help developers build, deploy, and manage Unity projects with greater efficiency and collaboration. These services include automated builds, cloud saves, version control, and performance analytics.

---

## 🔍 Core Services Explained

### 🚀 Cloud Build  
Unity Cloud Build automates game builds for multiple platforms. After pushing changes to your repository, Unity Cloud compiles your game remotely and notifies you when it’s done.

### 💾 Cloud Save  
Allows developers to store and sync user data (like game progress or settings) to the cloud across multiple devices.

### 🧩 Unity DevOps  
**Version Control (Plastic SCM)** and **Build Automation** enable teams to collaborate in real-time and ship code with confidence.

### 📊 Cloud Diagnostics and Analytics  
Offers real-time insights into player behavior and automated crash reporting.

---

## ⚙️ Setup Instructions

### Step 1: Create Unity Project  
1. Open Unity Hub.![Unity Dashboard Screenshot](images/unity_hub_dash.png)  
2. Click **New Project**, choose a 2D or 3D template.![Unity new project Screenshot](images/new_project.png)
  *make sure to enable "Use Unity Version Control" as well as "Respository details" and name your project repository*  
3. Name it (e.g., `UnityCloudDemo`) and click **Create**.

### Step 2: Activate Unity Services  
1. In Unity, go to `Window > Services`.  
2. Sign in and create a Project ID if needed.  
3. Enable:  
   - Cloud Build  
   - Cloud Save  
   - Cloud Diagnostics  
   - Analytics  

### Step 3: Configure Cloud Build  
1. Visit [Unity Cloud Dashboard](https://cloud.unity.com/build).  
2. Link your Unity project and connect your GitHub/GitLab repo.  
3. Create a build target (e.g., Android, WebGL).  
4. Set build triggers (e.g., on every push to `main`).

### Step 4: Set Up Cloud Save  
1. In Unity, go to `Window > Services > Cloud Save`.  
2. Enable the service.  
3. Example test code:
   ```csharp
   using Unity.Services.CloudSave;
   await CloudSaveService.Instance.Data.ForceSaveAsync();

## 🔐 Enable Version Control (Step 5)

### Option A: Plastic SCM

1. Go to **Unity Dashboard > DevOps > Version Control**.  
2. Create or link an organization.  
3. Install the Unity Version Control plugin (Plastic SCM).

### Option B: Git

1. Use your Git provider (e.g., GitHub, GitLab).  
2. Add a `.gitignore` file to exclude the following folders:

    ```
    Library/
    Temp/
    Builds/
    ```

---

## 💡 Best Practices

- ✅ Always enable **Collaborators** in your Unity Organization settings.  
- ✅ Use **environment variables** in build scripts for secrets and API keys.  
- ✅ Test **Cloud Save** functionality using development builds first.  
- ✅ Separate build targets for **staging** and **production** environments.  
- ✅ Regularly monitor **Cloud Diagnostics** for crash patterns.
- ✅ **Warning** Uploading large number of files through the web can be risky. The recommended best practice is to limit your web upload to 500 files max with a 20GB limit only. Alternatively, upload using Unity Version Control and then index your files.

## 🧯 Troubleshooting

| Issue                     | Solution                                                        |
|---------------------------|-----------------------------------------------------------------|
| Builds not triggering      | Ensure correct Git branch is linked and push includes new changes |
| Cloud Save errors          | Check internet connection and ensure Unity Authentication is enabled |
| Version control conflict   | Use lock rules or communicate with team before overwriting shared assets |
| Cloud Build stuck at “queued” | Free plan may delay builds during peak times                  |

## 🖼️ Screenshots


- Unity Dashboard showing Cloud Build targets  
  ![Unity Dashboard](path/to/unity_dashboard_screenshot.png)  

- In-Editor Service Panel with Cloud Save enabled  
  ![Cloud Save Panel](path/to/cloud_save_panel_screenshot.png)  

- Cloud Diagnostics console  
  ![Cloud Diagnostics](path/to/cloud_diagnostics_screenshot.png)  

- Sample success build email notification  
  ![Build Success Email](path/to/build_success_email.png)  

---

## 💰 Pricing

Unity Cloud Services offer different plans depending on your project's scale and requirements. Here is a general overview:

- **Free Plan**  
  - Limited number of Cloud Build minutes per month  
  - Basic Cloud Save storage quota  
  - Access to core features with usage caps  
  - Suitable for small projects or individual developers  

- **Plus and Pro Plans**  
  - Increased build minutes and storage limits  
  - Priority build queues  
  - Advanced analytics and diagnostics  
  - Access to collaboration features with more users  
  - Ideal for teams and larger projects  

- **Enterprise Plans**  
  - Custom pricing based on scale and support needs  
  - Dedicated support and SLAs  
  - Advanced security and compliance options  

**Note:** Pricing and limits can change; always check the [official Unity Cloud pricing page](https://unity.com/pricing) for the latest details.

Unity Cloud Services pricing varies by plan and usage. Below is an approximate summary:

| Plan        | Cost (USD)          | Cloud Build Minutes     | Cloud Save Storage          | Notes                              |
|-------------|---------------------|------------------------|----------------------------|-----------------------------------|
| **Free**    | $0/month            | 60 build minutes/month | 1 GB storage               | Basic features, ideal for small projects or individual developers |
| **Plus**    | $15/month           | 120 build minutes/month| 5 GB storage               | Priority build queue, more storage, collaboration for small teams |
| **Pro**     | $40/month           | 180 build minutes/month| 20 GB storage              | Advanced analytics, higher quotas, ideal for medium to large teams |
| **Enterprise** | Custom pricing    | Custom                 | Custom                     | Dedicated support, SLAs, compliance, for large-scale production teams |

> **Note:**  
> - Additional build minutes and storage can be purchased as add-ons.  
> - Pricing may vary based on region and contract terms.  
> - Always refer to the official [Unity Pricing Page](https://unity.com/pricing) for the most current info.

---

---

## 🧾 Conclusion

Unity Cloud Services simplify development workflows by handling builds, syncing data, and managing version control through a unified interface. Based on testing, the setup process is straightforward, but some services may require additional permissions or API calls.
