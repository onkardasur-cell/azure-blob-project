# 🚀 Azure Blob Storage + VM Web Server Integration Project

---

# 📌 **Project Overview**

This project demonstrates:

* ✅ Azure **Blob Storage (Object Storage)**
* ✅ Public access configuration
* ✅ Hosting static content (image)
* ✅ Azure VM (Ubuntu) as **Web Server**
* ✅ Integration of Blob URL into HTML page

---

# 🏗️ **Architecture**

```
Azure Blob Storage  --->  Public URL  --->  Apache Web Server (VM)  --->  Browser
       (cat.jpg)         (HTTPS)           (HTML Page)                 (User Access)
```

---

# 🧱 **Step 1: Create Azure Blob Storage**

### 🔹 Create Storage Account

* Go to **Azure Portal**
* Navigate to **Storage Accounts**
* Click **Create**

### 🔹 Configuration

| Setting     | Value              |
| ----------- | ------------------ |
| Performance | Standard           |
| Redundancy  | LRS (or as needed) |
| Access Tier | Hot                |
| Usage       | Cloud-native apps  |

---

# 📦 **Step 2: Create Container & Upload Object**

### 🔹 Create Container

* Name: `mycontainer`

### 🔹 Upload File

* Upload: `cat.jpg`

---

# 🌐 **Step 3: Enable Public Access**

### 🔓 Enable Anonymous Access

* Storage Account → **Settings**
* Enable:

  ```
  Allow Blob Anonymous Access = Enabled
  ```

### 🔓 Container Level Access

* Go to **Container → Change Access Level**
* Select:

  ```
  Blob (Read access for blobs only)
  ```

---

# 🔗 **Step 4: Copy Object URL**

```
https://storagegjg7879797.blob.core.windows.net/mycontainer/cat.jpg
```

✅ This URL will be used in your web application

---

# 💻 **Step 5: Azure VM Setup (Ubuntu Web Server)**

### 🔹 Connect to VM

```bash
cd Downloads
chmod 400 key.pem
ssh -i key.pem atul@74.249.11.32
```

---

# ⚙️ **Step 6: Install Apache Web Server**

```bash
sudo apt update -y
sudo apt install apache2 -y

sudo systemctl start apache2
sudo systemctl enable apache2
```

---

# 📁 **Step 7: Configure Web Directory**

```bash
cd /var/www/html

sudo chmod 755 /var/www/html
sudo rm index.html
sudo touch index.html
sudo nano index.html
```

---

# 🌐 **Step 8: HTML Page (Frontend)**

Paste the following code:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Cat Image</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
        }

        h1 {
            margin-top: 20px;
            color: #333;
        }

        img {
            margin-top: 20px;
            width: 400px;
            border-radius: 10px;
            box-shadow: 0px 4px 10px rgba(0,0,0,0.2);
        }

        .container {
            padding: 20px;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>🐱 My Cat Image from Azure Blob</h1>

        <img src="https://storagegjg7879797.blob.core.windows.net/mycontainer/cat.jpg" alt="Cat Image">

        <p>Hosted on Azure Blob Storage 🚀</p>
    </div>

</body>
</html>
```

---

# 🌍 **Step 9: Access Web Application**

Open in browser:

```
http://74.249.11.32/
```

---

# ✅ **Final Output**

* Apache serves HTML page
* Image is fetched from Azure Blob Storage
* Fully working **cloud-native static integration**

---

# 🎯 **Key Learning Outcomes**

| Concept             | Description              |
| ------------------- | ------------------------ |
| Object Storage      | Azure Blob Storage usage |
| Public Access       | Anonymous blob access    |
| Web Hosting         | Apache on Azure VM       |
| Integration         | HTML + Cloud Storage     |
| Real-world Use Case | Static asset hosting     |

---

# ⚠️ **Best Practices (Important for Production)**

* ❌ Avoid public access → Use **SAS Tokens / Private Endpoints**
* 🔐 Enable **HTTPS only**
* 📊 Use **Azure CDN** for performance
* 🛡️ Configure **NSG rules properly**
* 🔄 Use **CI/CD for deployment**

---

# 💡 **Enhancements (Next Level)**

* Add **Azure CDN**
* Use **Terraform for automation**
* Deploy via **Azure DevOps Pipeline**
* Add **Custom Domain + SSL**
* Use **Nginx instead of Apache**

---
