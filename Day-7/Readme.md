# 🚀 Install and Configure Nginx on Ubuntu (Step-by-Step Guide)

## 🟢 Step 1: Update System Packages

Before installing any software, update your system to get the latest packages.

```bash
sudo apt update
sudo apt upgrade -y
```

---

## 🟢 Step 2: Install Nginx

Install Nginx web server using:

```bash
sudo apt install nginx -y
```

---

## 🟢 Step 3: Start and Enable Nginx

Start the Nginx service and enable it to run on boot:

```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```

---

## 🟢 Step 4: Verify Nginx Installation

Check if Nginx is running:

```bash
sudo systemctl status nginx
```

👉 You can also open your browser and visit:

```
http://<your-public-ip>
```

You should see the default Nginx page.

---

## 🟢 Step 5: Create Custom HTML Page

Open the default web root file:

```bash
sudo vim /var/www/html/index.html
```

Replace with your HTML content:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Demo Page</title>
</head>
<body>
    <h1>I Learnt how networking works in Azure today 🚀</h1>
</body>
</html>
```

Save and exit:

* Press `ESC`
* Type `:wq`
* Press `Enter`

---

## 🟢 Step 6: Restart Nginx

Apply changes by restarting Nginx:

```bash
sudo systemctl restart nginx
```

---

## 🎉 Final Output

Visit:

```
http://<your-public-ip>
```

👉 Your custom HTML page is now LIVE on Nginx 🚀

---

## ⚠️ Troubleshooting

* Ensure **port 80 is open** in Azure NSG
* Check firewall:

```bash
sudo ufw allow 'Nginx Full'
```

* Restart service if needed:

```bash
sudo systemctl restart nginx
```

---

## 🎯 Quick Summary

```bash
Update → Install Nginx → Start Service → Add HTML → Restart → Access Website
```
