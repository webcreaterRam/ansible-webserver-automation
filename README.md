# Ansible Webserver Automation (Apache/Nginx)

This project automates webserver deployment (Apache or Nginx) on multiple Linux operating systems using Ansible roles. It detects OS family automatically, installs the correct package, deploys a dynamic HTML template, and ensures proper service startup using handlers.

---

## 📁 Project Structure

ansible-webserver-automation/
├── ansible.cfg
├── inventory
├── playbook.yml
└── roles/
    └── webserver/
        ├── defaults/
        │   └── main.yml
        ├── vars/
        │   └── main.yml
        ├── tasks/
        │   └── main.yml
        ├── handlers/
        │   └── main.yml
        └── templates/
            └── index.html.j2

---

## ⚙️ Variables Used

### defaults/main.yml
preferred_webserver: apache

### vars/main.yml
web_packages:
  Debian:
    apache:
      name: apache2
      service: apache2
      webroot: /var/www/html
    nginx:
      name: nginx
      service: nginx
      webroot: /usr/share/nginx/html

  RedHat:
    apache:
      name: httpd
      service: httpd
      webroot: /var/www/html
    nginx:
      name: nginx
      service: nginx
      webroot: /usr/share/nginx/html

---

## ▶️ Execution Flow

1. Detect OS family (Debian / RedHat)
2. Select correct package, service, and webroot
3. Install Apache or Nginx based on preferred_webserver
4. Create webroot directory
5. Deploy index.html template
6. Start + enable service
7. Handler restarts service only when template changes

---

## ▶️ Command to Run Playbook

ansible-playbook playbook.yml

---

## ▶️ Verify Deployment

ansible all -a "curl localhost"

Output Example:
<html>
<h1>Welcome from: <IP></h1>
<h1>Your OS : Ubuntu/AmazonLinux</h1>
</html>

---

## 🧩 Why This Project is Resume-Ready?

✔ Proper Ansible Role structure  
✔ OS auto-detection  
✔ Dynamic HTML deployment  
✔ Real multi-OS cross-platform automation  
✔ Clean, modular & idempotent  

---

## 👨‍💻 Author
Ramkumar Baghel  
GitHub: https://github.com/webcreaterRam

---

## 📜 License
MIT License
